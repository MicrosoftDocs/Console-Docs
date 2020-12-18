---
title: WriteConsole function
description: Writes a character string to a console screen buffer beginning at the current cursor location.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi/WriteConsole
- wincon/WriteConsole
- WriteConsole
- consoleapi/WriteConsoleA
- wincon/WriteConsoleA
- WriteConsoleA
- consoleapi/WriteConsoleW
- wincon/WriteConsoleW
- WriteConsoleW
MS-HAID:
- '_win32_writeconsole'
- 'base.writeconsole'
- 'consoles.writeconsole'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 1a13d9ef-75a9-49fd-9717-207f18612b59

topic_type:
- apiref
api_name:
- WriteConsole
- WriteConsoleA
- WriteConsoleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
---

# WriteConsole function

Writes a character string to a console screen buffer beginning at the current cursor location.

## Syntax

```C
BOOL WINAPI WriteConsole(
  _In_             HANDLE  hConsoleOutput,
  _In_       const VOID    *lpBuffer,
  _In_             DWORD   nNumberOfCharsToWrite,
  _Out_opt_        LPDWORD lpNumberOfCharsWritten,
  _Reserved_       LPVOID  lpReserved
);
```

## Parameters

*hConsoleOutput* \[in\]  
A handle to the console screen buffer. The handle must have the `GENERIC_WRITE` access right. For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).

*lpBuffer* \[in\]  
A pointer to a buffer that contains characters to be written to the console screen buffer. This is expected to be an array of either `char` for `WriteConsoleA` or `wchar_t` for `WriteConsoleW`.

*nNumberOfCharsToWrite* \[in\]  
The number of characters to be written. If the total size of the specified number of characters exceeds the available heap, the function fails with `ERROR_NOT_ENOUGH_MEMORY`.

*lpNumberOfCharsWritten* \[out, optional\]  
A pointer to a variable that receives the number of characters actually written.

*lpReserved*
Reserved; must be `NULL`.

## Return value

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [`GetLastError`](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## Remarks

The `WriteConsole` function writes characters to the console screen buffer at the current cursor position. The cursor position advances as characters are written. The [`SetConsoleCursorPosition`](setconsolecursorposition.md) function sets the current cursor position.

Characters are written using the foreground and background color attributes associated with the console screen buffer. The [`SetConsoleTextAttribute`](setconsoletextattribute.md) function changes these colors. To determine the current color attributes and the current cursor position, use [`GetConsoleScreenBufferInfo`](getconsolescreenbufferinfo.md).

All of the input modes that affect the behavior of the [`WriteFile`](https://msdn.microsoft.com/library/windows/desktop/aa365747) function have the same effect on `WriteConsole`. To retrieve and set the output modes of a console screen buffer, use the [`GetConsoleMode`](getconsolemode.md) and [`SetConsoleMode`](setconsolemode.md) functions.

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

`WriteConsole` fails if it is used with a standard handle that is redirected to a file. If an application processes multilingual output that can be redirected, determine whether the output handle is a console handle (one method is to call the [`GetConsoleMode`](getconsolemode.md) function and check whether it succeeds). If the handle is a console handle, call `WriteConsole`. If the handle is not a console handle, the output is redirected and you should call [`WriteFile`](https://msdn.microsoft.com/library/windows/desktop/aa365747) to perform the I/O. Be sure to prefix a Unicode plain text file with a byte order mark. For more information, see [Using Byte Order Marks](https://msdn.microsoft.com/library/windows/desktop/dd374101).

Although an application can use `WriteConsole` in ANSI mode to write ANSI characters, consoles do not support "ANSI escape" or "virtual terminal" sequences unless enabled. See [`Console Virtual Terminal Sequences`](console-virtual-terminal-sequences.md) for more information and for operating system version applicability.

When virtual terminal escape sequences are not enabled, console functions can provide equivalent functionality. For more information, see [`SetCursorPos`](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx), [`SetConsoleTextAttribute`](setconsoletextattribute.md), and [`GetConsoleCursorInfo`](getconsolecursorinfo.md).

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows 2000 Professional \[desktop apps only\] |
| Minimum supported server | Windows 2000 Server \[desktop apps only\] |
| Header | ConsoleApi.h (via WinCon.h, include Windows.h) |
| Library | Kernel32.lib |
| DLL | Kernel32.dll |
| Unicode and ANSI names | `WriteConsoleW` (Unicode) and `WriteConsoleA` (ANSI) |

## See also

[Console Functions](console-functions.md)

[`GetConsoleCursorInfo`](getconsolecursorinfo.md)

[`GetConsoleMode`](getconsolemode.md)

[`GetConsoleScreenBufferInfo`](getconsolescreenbufferinfo.md)

[Input and Output Methods](input-and-output-methods.md)

[`ReadConsole`](readconsole.md)

[`SetConsoleCP`](setconsolecp.md)

[`SetConsoleCursorPosition`](setconsolecursorposition.md)

[`SetConsoleMode`](setconsolemode.md)

[`SetConsoleOutputCP`](setconsoleoutputcp.md)

[`SetConsoleTextAttribute`](setconsoletextattribute.md)

[`SetCursorPos`](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx)

[`WriteFile`](https://msdn.microsoft.com/library/windows/desktop/aa365747)
