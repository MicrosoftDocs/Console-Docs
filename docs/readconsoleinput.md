---
title: ReadConsoleInput function
description: Reads data from a console input buffer and removes it from the buffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi/ReadConsoleInput
- wincon/ReadConsoleInput
- ReadConsoleInput
- consoleapi/ReadConsoleInputA
- wincon/ReadConsoleInputA
- ReadConsoleInputA
- consoleapi/ReadConsoleInputW
- wincon/ReadConsoleInputW
- ReadConsoleInputW
MS-HAID:
- '_win32_readconsoleinput'
- 'base.readconsoleinput'
- 'consoles.readconsoleinput'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 5a9f7b18-cdea-4041-a377-5532d30e0105

topic_type:
- apiref
api_name:
- ReadConsoleInput
- ReadConsoleInputA
- ReadConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
---

# ReadConsoleInput function

Reads data from a console input buffer and removes it from the buffer.

## Syntax

```C
BOOL WINAPI ReadConsoleInput(
  _In_  HANDLE        hConsoleInput,
  _Out_ PINPUT_RECORD lpBuffer,
  _In_  DWORD         nLength,
  _Out_ LPDWORD       lpNumberOfEventsRead
);
```

## Parameters

*hConsoleInput* \[in\]  
A handle to the console input buffer. The handle must have the `GENERIC_READ` access right. For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).

*lpBuffer* \[out\]  
A pointer to an array of [`INPUT_RECORD`](input-record-str.md) structures that receives the input buffer data.

*nLength* \[in\]  
The size of the array pointed to by the *lpBuffer* parameter, in array elements.

*lpNumberOfEventsRead* \[out\]  
A pointer to a variable that receives the number of input records read.

## Return value

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [`GetLastError`](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## Remarks

If the number of records requested in the *nLength* parameter exceeds the number of records available in the buffer, the number available is read. The function does not return until at least one input record has been read.

A process can specify a console input buffer handle in one of the [wait functions](https://msdn.microsoft.com/library/windows/desktop/ms687069) to determine when there is unread console input. When the input buffer is not empty, the state of a console input buffer handle is signaled.

To determine the number of unread input records in a console's input buffer, use the [`GetNumberOfConsoleInputEvents`](getnumberofconsoleinputevents.md) function. To read input records from a console input buffer without affecting the number of unread records, use the [`PeekConsoleInput`](peekconsoleinput.md) function. To discard all unread records in a console's input buffer, use the [`FlushConsoleInputBuffer`](flushconsoleinputbuffer.md) function.

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

## Examples

For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows 2000 Professional \[desktop apps only\] |
| Minimum supported server | Windows 2000 Server \[desktop apps only\] |
| Header | ConsoleApi.h (via WinCon.h, include Windows.h) |
| Library | Kernel32.lib |
| DLL | Kernel32.dll |
| Unicode and ANSI names | `ReadConsoleInputW` (Unicode) and `ReadConsoleInputA` (ANSI) |

## See also

[Console Functions](console-functions.md)

[`FlushConsoleInputBuffer`](flushconsoleinputbuffer.md)

[`GetNumberOfConsoleInputEvents`](getnumberofconsoleinputevents.md)

[`INPUT_RECORD`](input-record-str.md)

[Low-Level Console Input Functions](low-level-console-input-functions.md)

[`PeekConsoleInput`](peekconsoleinput.md)

[`ReadConsole`](readconsole.md)

[`ReadFile`](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[`SetConsoleCP`](setconsolecp.md)

[`SetConsoleOutputCP`](setconsoleoutputcp.md)

[`WriteConsoleInput`](writeconsoleinput.md)
