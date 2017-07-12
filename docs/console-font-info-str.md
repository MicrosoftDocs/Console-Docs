---
title: CONSOLE\_FONT\_INFO structure
description: Contains the index and size for a console font.
author: bitcrazed
ms.author: richturn
ms.topic: article
ms.prod: console
keywords: console, character mode applications, command line applications, terminal applications, console api
---

# CONSOLE\_FONT\_INFO structure


Contains information for a console font.

Syntax
------

```ManagedCPlusPlus
typedef struct _CONSOLE_FONT_INFO {
  DWORD nFont;
  COORD dwFontSize;
} CONSOLE_FONT_INFO, *PCONSOLE_FONT_INFO;
```

Members
-------

**nFont**  
The index of the font in the system's console font table.

**dwFontSize**  
A [**COORD**](coord-str.md) structure that contains the width and height of each character in the font, in logical units. The **X** member contains the width, while the **Y** member contains the height.

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

[**GetCurrentConsoleFont**](getcurrentconsolefont.md)

 

 




