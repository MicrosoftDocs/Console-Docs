---
title: CONSOLE_SCREEN_BUFFER_INFOEX structure
description: See reference information about the CONSOLE_SCREEN_BUFFER_INFOEX structure, which contains extended information about a console screen buffer.
author: miniksa
ms.author: miniksa
ms.topic: reference
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords: 
- consoleapi2/CONSOLE_SCREEN_BUFFER_INFOEX
- wincon/CONSOLE_SCREEN_BUFFER_INFOEX
- CONSOLE_SCREEN_BUFFER_INFOEX
- consoleapi2/PCONSOLE_SCREEN_BUFFER_INFOEX
- wincon/PCONSOLE_SCREEN_BUFFER_INFOEX
- PCONSOLE_SCREEN_BUFFER_INFOEX
MS-HAID:
- 'base.console\_screen\_buffer\_infoex'
- 'consoles.console\_screen\_buffer\_infoex'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 6ed40df3-063d-41c9-8637-510c95104603

topic_type:
- apiref
api_name:
- CONSOLE_SCREEN_BUFFER_INFOEX
api_location:
- WinCon.h
api_type:
- HeaderDef
---

# CONSOLE\_SCREEN\_BUFFER\_INFOEX structure

Contains extended information about a console screen buffer.

## Syntax

```C
typedef struct _CONSOLE_SCREEN_BUFFER_INFOEX {
  ULONG      cbSize;
  COORD      dwSize;
  COORD      dwCursorPosition;
  WORD       wAttributes;
  SMALL_RECT srWindow;
  COORD      dwMaximumWindowSize;
  WORD       wPopupAttributes;
  BOOL       bFullscreenSupported;
  COLORREF   ColorTable[16];
} CONSOLE_SCREEN_BUFFER_INFOEX, *PCONSOLE_SCREEN_BUFFER_INFOEX;
```

## Members

**cbSize**  
The size of this structure, in bytes.

**dwSize**  
A [**COORD**](coord-str.md) structure that contains the size of the console screen buffer, in character columns and rows.

**dwCursorPosition**  
A [**COORD**](coord-str.md) structure that contains the column and row coordinates of the cursor in the console screen buffer.

**wAttributes**  
The attributes of the characters written to a screen buffer by the [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) and [**WriteConsole**](writeconsole.md) functions, or echoed to a screen buffer by the [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) and [**ReadConsole**](readconsole.md) functions. For more information, see [Character Attributes](console-screen-buffers.md#character-attributes).

**srWindow**  
A [**SMALL\_RECT**](small-rect-str.md) structure that contains the console screen buffer coordinates of the upper-left and lower-right corners of the display window.

**dwMaximumWindowSize**  
A [**COORD**](coord-str.md) structure that contains the maximum size of the console window, in character columns and rows, given the current screen buffer size and font and the screen size.

**wPopupAttributes**  
The fill attribute for console pop-ups.

**bFullscreenSupported**  
If this member is `TRUE`, full-screen mode is supported; otherwise, it is not. This will always be `FALSE` for systems after Windows Vista with the [WDDM driver model](/windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model) as true direct VGA access to the monitor is no longer available.

**ColorTable**  
An array of [**COLORREF**](/windows/win32/gdi/colorref) values that describe the console's color settings.

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows Vista \[desktop apps only\] |
| Minimum supported server | Windows Server 2008 \[desktop apps only\] |
| Header | ConsoleApi2.h (via WinCon.h, include Windows.h) |

## See also

[**COORD**](coord-str.md)

[**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md)

[**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md)

[**SMALL\_RECT**](small-rect-str.md)
