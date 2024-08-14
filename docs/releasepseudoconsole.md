---
title: ReleasePseudoConsole function
description: See reference information about the ReleasePseudoConsole function, which allows the pseudoconsole to exit once all clients have disconnected.
author: lhecker
ms.author: lhecker
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api, conpty, pseudoconsole
f1_keywords:
- consoleapi/ReleasePseudoConsole
- ReleasePseudoConsole
topic_type:
- apiref
api_name:
- ReleasePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-2.dll
- KernelBase.dll
api_type:
- DllExport
---

# ReleasePseudoConsole function

Relinquishes ownership of the `HPCON` handle to the pseudoconsole, allowing it to automatically exit once all clients have disconnected.

## Syntax

```C
HRESULT WINAPI ReleasePseudoConsole(
    _In_ HPCON hPC
);
```

## Parameters

*hPC* \[in\]
A handle to an active pseudoconsole as opened by [CreatePseudoConsole](createpseudoconsole.md).

## Return value

Type: **HRESULT**

If this method succeeds, it returns **S_OK**. Otherwise, it returns an **HRESULT** error code.
The call is not expected to fail unless the **hPC** argument is invalid in which case it returns **E_INVALIDARG**.

## Remarks

Before this method was introduced, the initial pseudoconsole API was inherently flawed: **ClosePseudoConsole** would only exit until after the pseudoconsole has finished using the output pipe. This meant that the pseudoconsole effectively kept your application alive. The **HPCON** handle owned by your application on the other hand kept the pseudoconsole session alive until **ClosePseudoConsole** was called. This created a lifetime and ownership loop. The way applications were expected to break this loop up was by manually waiting for the spawned terminal processes to exit and then call **ClosePseudoConsole**. This made the API failure prone and resulted in shutdown deadlocks in various applications.

**ReleasePseudoConsole** solves this problem: It allows you to relinquish your half of the ownership. This in turn allows the pseudoconsole to automatically exit as soon as all clients have disconnected. All you need to do now is to read from or write to your output and input pipe handles until they return a failure. This indicates to you that all clients have disconnected and the the pseudoconsole is about to exit on its own.

> [!WARNING]
> **ReleasePseudoConsole** does not deallocate the memory associated with the **HPCON**. You must still call **ClosePseudoConsole** once you're done using the **HPCON** instance. See [ClosePseudoConsole](closepseudoconsole.md) for important information about its correct usage.

## Examples

For a full walkthrough on using this function to establish a pseudoconsole session, please see [Creating a Pseudoconsole Session](creating-a-pseudoconsole-session.md).

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows 11 24H2 (build 26100) \[desktop apps only\] |
| Minimum supported server | n/a |
| Header | ConsoleApi.h (via WinCon.h, include Windows.h) |
| Library | Kernel32.lib |
| DLL | Kernel32.dll |

## See also

[Pseudoconsoles](pseudoconsoles.md)

[Creating a Pseudoconsole Session](creating-a-pseudoconsole-session.md)

[**ClosePseudoConsole**](closepseudoconsole.md)
