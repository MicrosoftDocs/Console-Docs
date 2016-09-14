---
title: CONSOLE\_FONT\_INFOEX structure
description: Contains extended information for a console font.
MS-HAID:
- 'base.console\_font\_infoex'
- 'consoles.console\_font\_infoex'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: e9a087e1-264d-4d48-8adb-771a0e35b511
keywords: ["CONSOLE_FONT_INFOEX structure Consoles", "PCONSOLE_FONT_INFOEX structure pointer Consoles"]
topic_type:
- apiref
api_name:
- CONSOLE_FONT_INFOEX
api_location:
- Wincon.h
api_type:
- HeaderDef
---

# CONSOLE\_FONT\_INFOEX structure


Contains extended information for a console font.

Syntax
------

```ManagedCPlusPlus
typedef struct _CONSOLE_FONT_INFOEX {
  ULONG cbSize;
  DWORD nFont;
  COORD dwFontSize;
  UINT  FontFamily;
  UINT  FontWeight;
  WCHAR FaceName[LF_FACESIZE];
} CONSOLE_FONT_INFOEX, *PCONSOLE_FONT_INFOEX;
```

Members
-------

**cbSize**  
The size of this structure, in bytes.

**nFont**  
The index of the font in the system's console font table.

**dwFontSize**  
A [**COORD**](coord-str.md) structure that contains the width and height of each character in the font, in logical units. The **X** member contains the width, while the **Y** member contains the height.

**FontFamily**  
The font pitch and family. For information about the possible values for this member, see the description of the **tmPitchAndFamily** member of the [**TEXTMETRIC**](https://msdn.microsoft.com/library/windows/desktop/dd145132) structure.

**FontWeight**  
The font weight. The weight can range from 100 to 1000, in multiples of 100. For example, the normal weight is 400, while 700 is bold.

**FaceName**  
The name of the typeface (such as Courier or Arial).

Remarks
-------

To obtain the size of the font, pass the font index to the [**GetConsoleFontSize**](getconsolefontsize.md) function.

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
<td><p>Windows Vista [desktop apps only]</p></td>
</tr>
<tr class="even">
<td><p>Minimum supported server</p></td>
<td><p>Windows Server 2008 [desktop apps only]</p></td>
</tr>
<tr class="odd">
<td><p>Header</p></td>
<td>Wincon.h (include Windows.h)</td>
</tr>
</tbody>
</table>

## See also


[**GetCurrentConsoleFontEx**](getcurrentconsolefontex.md)

 

 




