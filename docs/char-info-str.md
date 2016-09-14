---
title: CHAR\_INFO structure
description: Specifies a Unicode or ANSI character and its attributes. This structure is used by console functions to read from and write to a console screen buffer.
MS-HAID:
- '\_win32\_char\_info\_str'
- 'base.char\_info\_str'
- 'consoles.char\_info\_str'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 5574a862-b262-41af-8862-e9837c5c7b5f
keywords: ["CHAR_INFO structure Consoles", "PCHAR_INFO structure pointer Consoles"]
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

```ManagedCPlusPlus
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
<td><a href="" id="foreground-blue"></a>
<strong>FOREGROUND_BLUE</strong>
0x0001</td>
<td><p>Text color contains blue.</p></td>
</tr>
<tr class="even">
<td><a href="" id="foreground-green"></a>
<strong>FOREGROUND_GREEN</strong>
0x0002</td>
<td><p>Text color contains green.</p></td>
</tr>
<tr class="odd">
<td><a href="" id="foreground-red"></a>
<strong>FOREGROUND_RED</strong>
0x0004</td>
<td><p>Text color contains red.</p></td>
</tr>
<tr class="even">
<td><a href="" id="foreground-intensity"></a>
<strong>FOREGROUND_INTENSITY</strong>
0x0008</td>
<td><p>Text color is intensified.</p></td>
</tr>
<tr class="odd">
<td><a href="" id="background-blue"></a>
<strong>BACKGROUND_BLUE</strong>
0x0010</td>
<td><p>Background color contains blue.</p></td>
</tr>
<tr class="even">
<td><a href="" id="background-green"></a>
<strong>BACKGROUND_GREEN</strong>
0x0020</td>
<td><p>Background color contains green.</p></td>
</tr>
<tr class="odd">
<td><a href="" id="background-red"></a>
<strong>BACKGROUND_RED</strong>
0x0040</td>
<td><p>Background color contains red.</p></td>
</tr>
<tr class="even">
<td><a href="" id="background-intensity"></a>
<strong>BACKGROUND_INTENSITY</strong>
0x0080</td>
<td><p>Background color is intensified.</p></td>
</tr>
<tr class="odd">
<td><a href="" id="common-lvb-leading-byte"></a>
<strong>COMMON_LVB_LEADING_BYTE</strong>
0x0100</td>
<td><p>Leading byte.</p></td>
</tr>
<tr class="even">
<td><a href="" id="common-lvb-trailing-byte"></a>
<strong>COMMON_LVB_TRAILING_BYTE</strong>
0x0200</td>
<td><p>Trailing byte.</p></td>
</tr>
<tr class="odd">
<td><a href="" id="common-lvb-grid-horizontal"></a>
<strong>COMMON_LVB_GRID_HORIZONTAL</strong>
0x0400</td>
<td><p>Top horizontal</p></td>
</tr>
<tr class="even">
<td><a href="" id="common-lvb-grid-lvertical"></a>
<strong>COMMON_LVB_GRID_LVERTICAL</strong>
0x0800</td>
<td><p>Left vertical.</p></td>
</tr>
<tr class="odd">
<td><a href="" id="common-lvb-grid-rvertical"></a>
<strong>COMMON_LVB_GRID_RVERTICAL</strong>
0x1000</td>
<td><p>Right vertical.</p></td>
</tr>
<tr class="even">
<td><a href="" id="common-lvb-reverse-video"></a>
<strong>COMMON_LVB_REVERSE_VIDEO</strong>
0x4000</td>
<td><p>Reverse foreground and background attribute.</p></td>
</tr>
<tr class="odd">
<td><a href="" id="common-lvb-underscore"></a>
<strong>COMMON_LVB_UNDERSCORE</strong>
0x8000</td>
<td><p>Underscore.</p></td>
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

## See also


[**ReadConsoleOutput**](readconsoleoutput.md)

[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)

 

 




