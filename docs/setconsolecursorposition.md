---
title: SetConsoleCursorPosition function
description: See reference information about the SetConsoleCursorPosition function, which sets the cursor position in the specified console screen buffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi2/SetConsoleCursorPosition
- wincon/SetConsoleCursorPosition
- SetConsoleCursorPosition
MS-HAID:
- '\_win32\_setconsolecursorposition'
- 'base.setconsolecursorposition'
- 'consoles.setconsolecursorposition'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 8e9abada-a64e-429f-8286-ced1169c7104

topic_type:
- apiref
api_name:
- SetConsoleCursorPosition
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
---

# SetConsoleCursorPosition function

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Sets the cursor position in the specified console screen buffer.

## Syntax

```C
BOOL WINAPI SetConsoleCursorPosition(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwCursorPosition
);
```

## Parameters

*hConsoleOutput* \[in\]  
A handle to the console screen buffer. The handle must have the `GENERIC\_READ` access right. For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).

*dwCursorPosition* \[in\]  
A [`COORD`](coord-str.md) structure that specifies the new cursor position, in characters. The coordinates are the column and row of a screen buffer character cell. The coordinates must be within the boundaries of the console screen buffer.

## Return value

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [`GetLastError`](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## Remarks

The cursor position determines where characters written by the [`WriteFile`](https://msdn.microsoft.com/library/windows/desktop/aa365747) or [`WriteConsole`](writeconsole.md) function, or echoed by the [`ReadFile`](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [`ReadConsole`](readconsole.md) function, are displayed. To determine the current position of the cursor, use the [`GetConsoleScreenBufferInfo`](getconsolescreenbufferinfo.md) function.

If the new cursor position is not within the boundaries of the console screen buffer's window, the window origin changes to make the cursor visible.

> [!TIP]
> This API has a `[virtual terminal](console-virtual-terminal-sequences.md)` equivalent in the `[simple cursor positioning](console-virtual-terminal-sequences.md#simple-cursor-positioning)` and `[cursor positioning](console-virtual-terminal-sequences.md#cursor-positioning)` sections. Use of the newline, carriage return, backspace, and tab control sequences can also assist with cursor positioning.

## Examples

For an example, see [Using the High-Level Input and Output Functions](using-the-high-level-input-and-output-functions.md).

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows 2000 Professional \[desktop apps only\] |
| Minimum supported server | Windows 2000 Server \[desktop apps only\] |
| Header | ConsoleApi2.h (via WinCon.h, include Windows.h) |
| Library | Kernel32.lib |
| DLL | Kernel32.dll |

## See also

[Console Functions](console-functions.md)

[Console Screen Buffers](console-screen-buffers.md)

[`GetConsoleCursorInfo`](getconsolecursorinfo.md)

[`GetConsoleScreenBufferInfo`](getconsolescreenbufferinfo.md)

[`ReadConsole`](readconsole.md)

[`ReadFile`](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[`SetConsoleCursorInfo`](setconsolecursorinfo.md)

[`WriteConsole`](writeconsole.md)

[`WriteFile`](https://msdn.microsoft.com/library/windows/desktop/aa365747)
