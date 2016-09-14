---
title: SMALL\_RECT structure
description: Defines the coordinates of the upper left and lower right corners of a rectangle.
MS-HAID:
- '\_win32\_small\_rect\_str'
- 'base.small\_rect\_str'
- 'consoles.small\_rect\_str'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 62639815-c7e9-4ae2-b152-61290f78422b
keywords: ["SMALL_RECT structure Consoles"]
topic_type:
- apiref
api_name:
- SMALL_RECT
api_location:
- Wincon.h
api_type:
- HeaderDef
---

# SMALL\_RECT structure


Defines the coordinates of the upper left and lower right corners of a rectangle.

Syntax
------

```ManagedCPlusPlus
typedef struct _SMALL_RECT {
  SHORT Left;
  SHORT Top;
  SHORT Right;
  SHORT Bottom;
} SMALL_RECT;
```

Members
-------

**Left**  
The x-coordinate of the upper left corner of the rectangle.

**Top**  
The y-coordinate of the upper left corner of the rectangle.

**Right**  
The x-coordinate of the lower right corner of the rectangle.

**Bottom**  
The y-coordinate of the lower right corner of the rectangle.

Remarks
-------

This structure is used by console functions to specify rectangular areas of console screen buffers, where the coordinates specify the rows and columns of screen-buffer character cells.

Examples
--------

For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).

Requirements
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Minimum supported client</p></td>
<td><p>Windows 2000 Professional [desktop apps only]</p></td>
</tr>
<tr class="even">
<td><p>Minimum supported server</p></td>
<td><p>Windows 2000 Server [desktop apps only]</p></td>
</tr>
<tr class="odd">
<td><p>Header</p></td>
<td>Wincon.h (include Windows.h)</td>
</tr>
</tbody>
</table>

## See also


[**RECT**](https://msdn.microsoft.com/library/windows/desktop/dd162897)

[**RECTL**](https://msdn.microsoft.com/library/windows/desktop/dd162907)

 

 




