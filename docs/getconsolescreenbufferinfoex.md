---
title: GetConsoleScreenBufferInfoEx function
description: Retrieves extended information about the specified console screen buffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi2/GetConsoleScreenBufferInfoEx
- wincon/GetConsoleScreenBufferInfoEx
- GetConsoleScreenBufferInfoEx
MS-HAID:
- 'base.getconsolescreenbufferinfoex'
- 'consoles.getconsolescreenbufferinfoex'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 60534226-d26f-44e2-a4cc-64811882e308

topic_type:
- apiref
api_name:
- GetConsoleScreenBufferInfoEx
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
---

# GetConsoleScreenBufferInfoEx function

Retrieves extended information about the specified console screen buffer.

## Syntax

```C
BOOL WINAPI GetConsoleScreenBufferInfoEx(
  _In_  HANDLE                        hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFOEX lpConsoleScreenBufferInfoEx
);
```

## Parameters

*hConsoleOutput* \[in\]  
A handle to the console screen buffer. The handle must have the `GENERIC\_READ` access right. For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).

*lpConsoleScreenBufferInfoEx* \[out\]  
A [`CONSOLE\_SCREEN\_BUFFER\_INFOEX`](console-screen-buffer-infoex.md) structure that receives the requested console screen buffer information.

## Return value

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [`GetLastError`](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## Remarks

The rectangle returned in the `srWindow` member of the [`CONSOLE\_SCREEN\_BUFFER\_INFOEX`](console-screen-buffer-infoex.md) structure can be modified and then passed to the [`SetConsoleWindowInfo`](setconsolewindowinfo.md) function to scroll the console screen buffer in the window, to change the size of the window, or both.

All coordinates returned in the [`CONSOLE\_SCREEN\_BUFFER\_INFOEX`](console-screen-buffer-infoex.md) structure are in character-cell coordinates, where the origin (0, 0) is at the upper-left corner of the console screen buffer.

> [!TIP]
> This API does not have a `[virtual terminal](console-virtual-terminal-sequences.md)` equivalent. Its use may still be required for applications that are attempting to draw columns, grids, or fill the display to retrieve the window size. This window state is managed by the TTY/PTY/Pseudoconsole outside of the normal stream flow and is generally considered a user privilege not adjustable by the client application. Updates can be received on [`ReadConsoleInput`](readconsoleinput.md).

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows Vista \[desktop apps only\] |
| Minimum supported server | Windows Server 2008 \[desktop apps only\] |
| Header | ConsoleApi2.h (via WinCon.h, include Windows.h) |
| Library | Kernel32.lib |
| DLL | Kernel32.dll |

## See also

[Console Functions](console-functions.md)

[`CONSOLE\_SCREEN\_BUFFER\_INFOEX`](console-screen-buffer-infoex.md)

[`SetConsoleScreenBufferInfoEx`](setconsolescreenbufferinfoex.md)
