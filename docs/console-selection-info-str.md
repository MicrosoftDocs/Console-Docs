---
title: CONSOLE\_SELECTION\_INFO structure
description: Contains information for a console selection.
author: bitcrazed
ms.author: richturn;miniksa


MS-HAID:
- '\_win32\_console\_selection\_info\_str'
- 'base.console\_selection\_info\_str'
- 'consoles.console\_selection\_info\_str'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 9530b249-8db4-4516-9cc8-2b452c6751f9
keywords: ["CONSOLE_SELECTION_INFO structure Consoles", "PCONSOLE_SELECTION_INFO structure pointer Consoles"]
topic_type:
- apiref
api_name:
- CONSOLE_SELECTION_INFO
api_location:
- Wincon.h
api_type:
- HeaderDef
---

# CONSOLE\_SELECTION\_INFO structure


Contains information for a console selection.

Syntax
------

```ManagedCPlusPlus
typedef struct _CONSOLE_SELECTION_INFO {
  DWORD      dwFlags;
  COORD      dwSelectionAnchor;
  SMALL_RECT srSelection;
} CONSOLE_SELECTION_INFO, *PCONSOLE_SELECTION_INFO;
```

Members
-------

**dwFlags**  
The selection indicator. This member can be one or more of the following values.

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
<td><span id="CONSOLE_MOUSE_DOWN"></span><span id="console_mouse_down"></span>
<strong>CONSOLE_MOUSE_DOWN</strong>
0x0008</td>
<td><p>Mouse is down</p></td>
</tr>
<tr class="even">
<td><span id="CONSOLE_MOUSE_SELECTION"></span><span id="console_mouse_selection"></span>
<strong>CONSOLE_MOUSE_SELECTION</strong>
0x0004</td>
<td><p>Selecting with the mouse</p></td>
</tr>
<tr class="odd">
<td><span id="CONSOLE_NO_SELECTION"></span><span id="console_no_selection"></span>
<strong>CONSOLE_NO_SELECTION</strong>
0x0000</td>
<td><p>No selection</p></td>
</tr>
<tr class="even">
<td><span id="CONSOLE_SELECTION_IN_PROGRESS"></span><span id="console_selection_in_progress"></span>
<strong>CONSOLE_SELECTION_IN_PROGRESS</strong>
0x0001</td>
<td><p>Selection has begun</p></td>
</tr>
<tr class="odd">
<td><span id="CONSOLE_SELECTION_NOT_EMPTY"></span><span id="console_selection_not_empty"></span>
<strong>CONSOLE_SELECTION_NOT_EMPTY</strong>
0x0002</td>
<td><p>Selection rectangle is not empty</p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

**dwSelectionAnchor**  
A [**COORD**](coord-str.md) structure that specifies the selection anchor, in characters.

**srSelection**  
A [**SMALL\_RECT**](small-rect-str.md) structure that specifies the selection rectangle.

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
<td><p>Windows XP [desktop apps only]</p></td>
</tr>
<tr class="even">
<td><p>Minimum supported server</p></td>
<td><p>Windows Server 2003 [desktop apps only]</p></td>
</tr>
<tr class="odd">
<td><p>Header</p></td>
<td>Wincon.h (include Windows.h)</td>
</tr>
</tbody>
</table>

## <span id="see_also"></span>See also


[**COORD**](coord-str.md)

[**GetConsoleSelectionInfo**](getconsoleselectioninfo.md)

[**SMALL\_RECT**](small-rect-str.md)

 

 




