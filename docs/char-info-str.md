---
title: CHAR_INFO structure
description: Specifies a Unicode or ANSI character and its attributes. This structure is used by console functions to read from and write to a console screen buffer.
author: bitcrazed
ms.author: richturn
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- WINCONTYPES/PCHAR_INFO
- PCHAR_INFO
MS-HAID:
- '\_win32\_char\_info\_str'
- 'base.char\_info\_str'
- 'consoles.char\_info\_str'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 5574a862-b262-41af-8862-e9837c5c7b5f
topic_type:
- apiref
api_name:
- CHAR_INFO
api_location:
- Wincon.h
api_type:
- HeaderDef
---

# CHAR\_INFO structure


Specifies a Unicode or ANSI character and its attributes. This structure is used by console functions to read from and write to a console screen buffer.

Syntax
------

```C
typedef struct _CHAR_INFO {
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } Char;
  WORD  Attributes;
} CHAR_INFO, *PCHAR_INFO;
```

Members
-------

**Char**  
A union of the following members.

**UnicodeChar**  
Unicode character of a screen buffer character cell.

**AsciiChar**  
ANSI character of a screen buffer character cell.

**Attributes**  
The character attributes. This member can be zero or any combination of the following values.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Value</th>
<th>Meaning</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="FOREGROUND_BLUE"></span><span id="foreground_blue"></span>
<strong>FOREGROUND_BLUE</strong>
0x0001</td>
<td><p>Text color contains blue.</p></td>
</tr>
<tr class="even">
<td><span id="FOREGROUND_GREEN"></span><span id="foreground_green"></span>
<strong>FOREGROUND_GREEN</strong>
0x0002</td>
<td><p>Text color contains green.</p></td>
</tr>
<tr class="odd">
<td><span id="FOREGROUND_RED"></span><span id="foreground_red"></span>
<strong>FOREGROUND_RED</strong>
0x0004</td>
<td><p>Text color contains red.</p></td>
</tr>
<tr class="even">
<td><span id="FOREGROUND_INTENSITY"></span><span id="foreground_intensity"></span>
<strong>FOREGROUND_INTENSITY</strong>
0x0008</td>
<td><p>Text color is intensified.</p></td>
</tr>
<tr class="odd">
<td><span id="BACKGROUND_BLUE"></span><span id="background_blue"></span>
<strong>BACKGROUND_BLUE</strong>
0x0010</td>
<td><p>Background color contains blue.</p></td>
</tr>
<tr class="even">
<td><span id="BACKGROUND_GREEN"></span><span id="background_green"></span>
<strong>BACKGROUND_GREEN</strong>
0x0020</td>
<td><p>Background color contains green.</p></td>
</tr>
<tr class="odd">
<td><span id="BACKGROUND_RED"></span><span id="background_red"></span>
<strong>BACKGROUND_RED</strong>
0x0040</td>
<td><p>Background color contains red.</p></td>
</tr>
<tr class="even">
<td><span id="BACKGROUND_INTENSITY"></span><span id="background_intensity"></span>
<strong>BACKGROUND_INTENSITY</strong>
0x0080</td>
<td><p>Background color is intensified.</p></td>
</tr>
<tr class="odd">
<td><span id="COMMON_LVB_LEADING_BYTE"></span><span id="common_lvb_leading_byte"></span>
<strong>COMMON_LVB_LEADING_BYTE</strong>
0x0100</td>
<td><p>Leading byte.</p></td>
</tr>
<tr class="even">
<td><span id="COMMON_LVB_TRAILING_BYTE"></span><span id="common_lvb_trailing_byte"></span>
<strong>COMMON_LVB_TRAILING_BYTE</strong>
0x0200</td>
<td><p>Trailing byte.</p></td>
</tr>
<tr class="odd">
<td><span id="COMMON_LVB_GRID_HORIZONTAL"></span><span id="common_lvb_grid_horizontal"></span>
<strong>COMMON_LVB_GRID_HORIZONTAL</strong>
0x0400</td>
<td><p>Top horizontal</p></td>
</tr>
<tr class="even">
<td><span id="COMMON_LVB_GRID_LVERTICAL"></span><span id="common_lvb_grid_lvertical"></span>
<strong>COMMON_LVB_GRID_LVERTICAL</strong>
0x0800</td>
<td><p>Left vertical.</p></td>
</tr>
<tr class="odd">
<td><span id="COMMON_LVB_GRID_RVERTICAL"></span><span id="common_lvb_grid_rvertical"></span>
<strong>COMMON_LVB_GRID_RVERTICAL</strong>
0x1000</td>
<td><p>Right vertical.</p></td>
</tr>
<tr class="even">
<td><span id="COMMON_LVB_REVERSE_VIDEO"></span><span id="common_lvb_reverse_video"></span>
<strong>COMMON_LVB_REVERSE_VIDEO</strong>
0x4000</td>
<td><p>Reverse foreground and background attribute.</p></td>
</tr>
<tr class="odd">
<td><span id="COMMON_LVB_UNDERSCORE"></span><span id="common_lvb_underscore"></span>
<strong>COMMON_LVB_UNDERSCORE</strong>
0x8000</td>
<td><p>Underscore.</p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

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

## <span id="see_also"></span>See also


[**ReadConsoleOutput**](readconsoleoutput.md)

[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)

 

 




