---
title: CreateConsoleScreenBuffer function
description: CreateConsoleScreenBuffer function creates a screen buffer for the Windows Console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi2/CreateConsoleScreenBuffer
- wincon/CreateConsoleScreenBuffer
- CreateConsoleScreenBuffer
MS-HAID:
- '\_win32\_createconsolescreenbuffer'
- 'base.createconsolescreenbuffer'
- 'consoles.createconsolescreenbuffer'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 98bb74e4-dad2-4615-9263-48ba778a06ff

topic_type:
- apiref
api_name:
- CreateConsoleScreenBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
---

# CreateConsoleScreenBuffer function

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Creates a console screen buffer.

## Syntax

```C
HANDLE WINAPI CreateConsoleScreenBuffer(
  _In_             DWORD               dwDesiredAccess,
  _In_             DWORD               dwShareMode,
  _In_opt_   const SECURITY_ATTRIBUTES *lpSecurityAttributes,
  _In_             DWORD               dwFlags,
  _Reserved_       LPVOID              lpScreenBufferData
);
```

## Parameters

*dwDesiredAccess* \[in\]  
The access to the console screen buffer. For a list of access rights, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).

*dwShareMode* \[in\]  
This parameter can be zero, indicating that the buffer cannot be shared, or it can be one or more of the following values.

| Value | Meaning |
|-|-|
| **FILE_SHARE_READ** 0x00000001 | Other open operations can be performed on the console screen buffer for read access. |
| **FILE_SHARE_WRITE** 0x00000002 | Other open operations can be performed on the console screen buffer for write access. |

*lpSecurityAttributes* \[in, optional\]  
A pointer to a [**SECURITY\_ATTRIBUTES**](https://msdn.microsoft.com/library/windows/desktop/aa379560) structure that determines whether the returned handle can be inherited by child processes. If *lpSecurityAttributes* is **NULL**, the handle cannot be inherited. The **lpSecurityDescriptor** member of the structure specifies a security descriptor for the new console screen buffer. If *lpSecurityAttributes* is **NULL**, the console screen buffer gets a default security descriptor. The ACLs in the default security descriptor for a console screen buffer come from the primary or impersonation token of the creator.

*dwFlags* \[in\]  
The type of console screen buffer to create. The only supported screen buffer type is **CONSOLE\_TEXTMODE\_BUFFER**.

*lpScreenBufferData*  
Reserved; should be **NULL**.

## Return value

If the function succeeds, the return value is a handle to the new console screen buffer.

If the function fails, the return value is **INVALID\_HANDLE\_VALUE**. To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## Remarks

A console can have multiple screen buffers but only one active screen buffer. Inactive screen buffers can be accessed for reading and writing, but only the active screen buffer is displayed. To make the new screen buffer the active screen buffer, use the [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) function.

The newly created screen buffer will copy some properties from the active screen buffer at the time that this function is called. The behavior is as follows:

- `Font` - copied from active screen buffer
- `Display Window Size` - copied from active screen buffer
- `Buffer Size` - matched to `Display Window Size` (**NOT** copied)
- `Default Attributes` (colors) - copied from active screen buffer
- `Default Popup Attributes` (colors) - copied from active screen buffer

The calling process can use the returned handle in any function that requires a handle to a console screen buffer, subject to the limitations of access specified by the *dwDesiredAccess* parameter.

The calling process can use the [**DuplicateHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724251) function to create a duplicate screen buffer handle that has different access or inheritability from the original handle. However, **DuplicateHandle** cannot be used to create a duplicate that is valid for a different process (except through inheritance).

To close the console screen buffer handle, use the [**CloseHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724211) function.

> [!TIP]
> This API is not recommended but it does have an approximate **[virtual terminal](console-virtual-terminal-sequences)** equivalent in the **[alternate screen buffer](console-virtual-terminal-sequences#alternate-screen-buffer)** sequence. Setting the _alternate screen buffer_ can provide an application with a separate, isolated space for drawing over the course of its session runtime while preserving the content that was displayed by the application's invoker. This maintains that drawing information for simple restoration on process exit.

## Examples

For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).

## Requirements

| | |
|-|-|
| Minimum supported client | Windows 2000 Professional \[desktop apps only\] |
| Minimum supported server | Windows 2000 Server \[desktop apps only\] |
| Header | ConsoleApi2.h (via WinCon.h, include Windows.h) |
| Library | Kernel32.lib |
| DLL | Kernel32.dll |

## See also

[Console Functions](console-functions.md)

[Console Screen Buffers](console-screen-buffers.md)

[**CloseHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724211)

[**DuplicateHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724251)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**SECURITY\_ATTRIBUTES**](https://msdn.microsoft.com/library/windows/desktop/aa379560)

[**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md)

[**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md)
