---
title: COORD structure
description: Defines the coordinates of a character cell in a console screen buffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- wincontypes/COORD
- wincon/COORD
- COORD
- wincontypes/PCOORD
- wincon/PCOORD
- PCOORD
MS-HAID:
- '\_win32\_coord\_str'
- 'base.coord\_str'
- 'consoles.coord\_str'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: d730c46e-ea17-475e-b956-8ee5f4f5c04e

topic_type:
- apiref
api_name:
- COORD
api_location:
- WinCon.h
api_type:
- HeaderDef
---

# COORD structure

Defines the coordinates of a character cell in a console screen buffer. The origin of the coordinate system (0,0) is at the top, left cell of the buffer.

## Syntax

```C
typedef struct _COORD {
  SHORT X;
  SHORT Y;
} COORD, *PCOORD;
```

## Members

**X**  
The horizontal coordinate or column value. The units depend on the function call.

**Y**  
The vertical coordinate or row value. The units depend on the function call.

## Examples

For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).

## Requirements

| | |
|-|-|
| Minimum supported client | Windows 2000 Professional \[desktop apps only\] |
| Minimum supported server | Windows 2000 Server \[desktop apps only\] |
| Header | WinConTypes.h (via WinCon.h, include Windows.h) |

## See also

[**CONSOLE\_FONT\_INFO**](console-font-info-str.md)

[**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md)

[**CONSOLE\_SELECTION\_INFO**](console-selection-info-str.md)

[**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md)

[**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md)

[**GetConsoleFontSize**](getconsolefontsize.md)

[**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md)

[**MOUSE\_EVENT\_RECORD**](mouse-event-record-str.md)

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md)

[**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md)

[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md)

[**SetConsoleCursorPosition**](setconsolecursorposition.md)

[**SetConsoleDisplayMode**](setconsoledisplaymode.md)

[**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md)

[**WINDOW\_BUFFER\_SIZE\_RECORD**](window-buffer-size-record-str.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)

[**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md)

[**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)
