---
title: GetConsoleDisplayMode function
description: See reference information about the GetConsoleDisplayMode function, which retrieves the display mode of the current console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi3/GetConsoleDisplayMode
- wincon/GetConsoleDisplayMode
- GetConsoleDisplayMode
MS-HAID:
- '\_win32\_getconsoledisplaymode'
- 'base.getconsoledisplaymode'
- 'consoles.getconsoledisplaymode'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: e19ff900-a671-41d3-a9c8-9e4507c47eff

topic_type:
- apiref
api_name:
- GetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
---

# GetConsoleDisplayMode function

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Retrieves the display mode of the current console.

## Syntax

```C
BOOL WINAPI GetConsoleDisplayMode(
  _Out_ LPDWORD lpModeFlags
);
```

## Parameters

*lpModeFlags* \[out\]  
The display mode of the console. This parameter can be one or more of the following values.

| Value | Meaning |
|-|-|
| **CONSOLE_FULLSCREEN** 1 | Full-screen console. The console is in this mode as soon as the window is maximized. At this point, the transition to full-screen mode can still fail. |
| **CONSOLE_FULLSCREEN_HARDWARE** 2 | Full-screen console communicating directly with the video hardware. This mode is set after the console is in **CONSOLE_FULLSCREEN** mode to indicate that the transition to full-screen mode has completed. |

> [!NOTE]
> The transition to a 100% full screen video hardware mode was removed in Windows Vista (TODO: citation needed) with the replatforming of the graphics stack to WDDM (TODO: insert link). On later versions of Windows, the maximum resulting state is **CONSOLE_FULLSCREEN** representing a frameless window that appears full screen but isn't in exclusive control of the hardware.

## Return value

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## Remarks

To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later. For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).

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

[**SetConsoleDisplayMode**](setconsoledisplaymode.md)
