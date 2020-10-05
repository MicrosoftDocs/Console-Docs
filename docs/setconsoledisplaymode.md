---
title: SetConsoleDisplayMode function
description: See reference information about the SetConsoleDisplayMode function, which sets the display mode of the specified console screen buffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi3/SetConsoleDisplayMode
- wincon/SetConsoleDisplayMode
- SetConsoleDisplayMode
MS-HAID:
- 'base.setconsoledisplaymode'
- 'consoles.setconsoledisplaymode'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 27437a85-f784-41fc-8279-9fe089b0a744

topic_type:
- apiref
api_name:
- SetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
---

# SetConsoleDisplayMode function

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Sets the display mode of the specified console screen buffer.

## Syntax

```C
BOOL WINAPI SetConsoleDisplayMode(
  _In_      HANDLE hConsoleOutput,
  _In_      DWORD  dwFlags,
  _Out_opt_ PCOORD lpNewScreenBufferDimensions
);
```

## Parameters

*hConsoleOutput* \[in\]  
A handle to the console screen buffer.

*dwFlags* \[in\]  
The display mode of the console. This parameter can be one or more of the following values.

| Value | Meaning |
|-|-|
| **CONSOLE_FULLSCREEN_MODE** 1 | Text is displayed in full-screen mode. |
| **CONSOLE_WINDOWED_MODE** 2 | Text is displayed in a console window. |

*lpNewScreenBufferDimensions* \[out, optional\]  
A pointer to a [**COORD**](coord-str.md) structure that receives the new dimensions of the screen buffer, in characters.

## Return value

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## Requirements

| | |
|-|-|
| Minimum supported client | Windows XP \[desktop apps only\] |
| Minimum supported server | Windows Server 2003 \[desktop apps only\] |
| Header | ConsoleApi3.h (via WinCon.h, include Windows.h) |
| Library | Kernel32.lib |
| DLL | Kernel32.dll |

## See also

[Console Functions](console-functions.md)

[Console Modes](console-modes.md)

[**GetConsoleDisplayMode**](getconsoledisplaymode.md)
