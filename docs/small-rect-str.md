---
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- wincontypes/SMALL_RECT
- wincon/SMALL_RECT
- SMALL_RECT
title: SMALL_RECT structure
description: Defines the coordinates of the upper left and lower right corners of a rectangle.
MS-HAID:
- '\_win32\_small\_rect\_str'
- 'base.small\_rect\_str'
- 'consoles.small\_rect\_str'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 62639815-c7e9-4ae2-b152-61290f78422b

topic_type:
- apiref
api_name:
- SMALL_RECT
api_location:
- WinCon.h
api_type:
- HeaderDef
---

# SMALL\_RECT structure

Defines the coordinates of the upper left and lower right corners of a rectangle.

## Syntax

```C
typedef struct _SMALL_RECT {
  SHORT Left;
  SHORT Top;
  SHORT Right;
  SHORT Bottom;
} SMALL_RECT;
```

## Members

**Left**  
The x-coordinate of the upper left corner of the rectangle.

**Top**  
The y-coordinate of the upper left corner of the rectangle.

**Right**  
The x-coordinate of the lower right corner of the rectangle.

**Bottom**  
The y-coordinate of the lower right corner of the rectangle.

## Remarks

This structure is used by console functions to specify rectangular areas of console screen buffers, where the coordinates specify the rows and columns of screen-buffer character cells.

## Examples

For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows 2000 Professional \[desktop apps only\] |
| Minimum supported server | Windows 2000 Server \[desktop apps only\] |
| Header | WinConTypes.h (via WinCon.h, include Windows.h) |

## See also

[**RECT**](/previous-versions//dd162897(v=vs.85))

[**RECTL**](/previous-versions//dd162907(v=vs.85))