---
title: CONSOLE_SCREEN_BUFFER_INFO structure
description: See reference information about the CONSOLE_SCREEN_BUFFER_INFO structure, which contains information about a console screen buffer.
author: miniksa
ms.author: miniksa
ms.topic: reference
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords: 
- consoleapi2/CONSOLE_SCREEN_BUFFER_INFO
- wincon/CONSOLE_SCREEN_BUFFER_INFO
- CONSOLE_SCREEN_BUFFER_INFO
- consoleapi2/PCONSOLE_SCREEN_BUFFER_INFO
- wincon/PCONSOLE_SCREEN_BUFFER_INFO
- PCONSOLE_SCREEN_BUFFER_INFO
MS-HAID:
- '\_win32\_console\_screen\_buffer\_info\_str'
- 'base.console\_screen\_buffer\_info\_str'
- 'consoles.console\_screen\_buffer\_info\_str'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 586b3e0f-2f6b-4a03-b8e4-602a892be56d

topic_type:
- apiref
api_name:
- CONSOLE_SCREEN_BUFFER_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
---

# CONSOLE\_SCREEN\_BUFFER\_INFO structure

Contains information about a console screen buffer.

## Syntax

```C
typedef struct _CONSOLE_SCREEN_BUFFER_INFO {
  COORD      dwSize;
  COORD      dwCursorPosition;
  WORD       wAttributes;
  SMALL_RECT srWindow;
  COORD      dwMaximumWindowSize;
} CONSOLE_SCREEN_BUFFER_INFO;
```

## Members

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

## Examples

For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows 2000 Professional \[desktop apps only\] |
| Minimum supported server | Windows 2000 Server \[desktop apps only\] |
| Header | ConsoleApi2.h (via WinCon.h, include Windows.h) |

## See also

[**COORD**](coord-str.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**ReadConsole**](readconsole.md)

[**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile)

[**SMALL\_RECT**](small-rect-str.md)

[**WriteConsole**](writeconsole.md)

[**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile)
