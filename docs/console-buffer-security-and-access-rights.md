---
title: Console Buffer Security and Access Rights
description: The Windows security model enables you to control access to console input buffers and console screen buffers. For more information about security, see Access-Control Model.
author: miniksa
ms.author: miniksa
ms.topic: how-to
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- '\_win32\_console\_buffer\_security\_and\_access\_rights'
- 'base.console\_buffer\_security\_and\_access\_rights'
- 'consoles.console\_buffer\_security\_and\_access\_rights'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: f9a50063-8fc8-4cd1-8f24-9ae3946d3119
---

# Console Buffer Security and Access Rights

The Windows security model enables you to control access to console input buffers and console screen buffers. For more information about security, see [Access-Control Model](/windows/win32/secauthz/access-control-model).

## Console Object Security Descriptors

You can specify a [security descriptor](/windows/win32/secauthz/security-descriptors) for the console input and console screen buffers when you call the [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) or [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) function. If you specify **NULL**, the object gets a default security descriptor. The ACLs in the default security descriptor for a console buffer come from the primary or impersonation token of the creator.

The handles returned by [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea), [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md), and [**GetStdHandle**](getstdhandle.md) have the **GENERIC\_READ** and **GENERIC\_WRITE** access rights.

The valid access rights include the **GENERIC\_READ** and **GENERIC\_WRITE** [generic access rights](/windows/win32/secauthz/generic-access-rights).

| Value | Meaning |
|-|-|
| **GENERIC\_READ** (0x80000000L)  | Requests read access to the console screen buffer, enabling the process to read data from the buffer. |
| **GENERIC\_WRITE** (0x40000000L) | Requests write access to the console screen buffer, enabling the process to write data to the buffer. |

> [!NOTE]
> **[Universal Windows Platform console apps](/windows/uwp/launch-resume/console-uwp)** and those with a lower **[integrity level](/windows/win32/secauthz/mandatory-integrity-control)** than the attached console will be prohibited from both reading the output buffer and writing to the input buffer even if the security descriptors above would normally permit it. Please see the **[Wrong Way Verbs](#wrong-way-verbs)** discussion below for more details.

## Wrong-Way Verbs

Some operations to the console objects will be denied even if the object has a security descriptor that is stated to specifically permit reading or writing. This specifically concerns command-line applications running in a reduced-privilege context that are sharing a console session that was created by a command-line application in a more permissive context.

The term "wrong-way verbs" is intended to apply to the operation that is the converse of the normal flow for one of the console objects. Specifically, the normal flow for the output buffer is writing and the normal flow for the input buffer is reading. The "wrong-way" would therefore be the reading of the output buffer or the writing of the input buffer. These are functions that are described in the **[Low-Level Console I/O Functions](low-level-console-i-o.md)** documentation.

The two scenarios where this can be found are:

1. **[Universal Windows Platform console apps](/windows/uwp/launch-resume/console-uwp)**. As these are cousins of other Universal Windows Platform applications, they hold a promise that they are isolated from other applications and provide user guarantees around the effects of their operation.
1. Any console application intentionally launched with a lower **[integrity level](/windows/win32/secauthz/mandatory-integrity-control)** than the existing session which can be accomplished with **[labeling or token manipulation during CreateProcess](/previous-versions/dotnet/articles/bb625960(v=msdn.10))**.

If either of these scenarios is detected, the console will apply the "wrong-way verbs" flag to the command-line application connection and reject calls to the following APIs to reduce the surface of communication between the levels:

:::row:::
    :::column:::
        [ReadConsoleOutput](readconsoleoutput.md)  
        [ReadConsoleOutputCharacter](readconsoleoutputcharacter.md)  
        [ReadConsoleOutputAttribute](readconsoleoutputattribute.md)  
    :::column-end:::
    :::column:::
        [WriteConsoleInput](writeconsoleinput.md)  
    :::column-end:::
:::row-end:::

Rejected calls will receive an **access denied** error code, the same as if the read or write permission were denied by the security descriptors on the object.
