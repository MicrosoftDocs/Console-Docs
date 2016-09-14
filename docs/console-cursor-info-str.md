---
title: CONSOLE\_CURSOR\_INFO structure
description: Contains information about the console cursor.
MS-HAID:
- '\_win32\_console\_cursor\_info\_str'
- 'base.console\_cursor\_info\_str'
- 'consoles.console\_cursor\_info\_str'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 0e71ce8c-e008-4bd7-922e-c44484b425ef
keywords: ["CONSOLE_CURSOR_INFO structure Consoles", "PCONSOLE_CURSOR_INFO structure pointer Consoles"]
topic_type:
- apiref
api_name:
- CONSOLE_CURSOR_INFO
api_location:
- Wincon.h
api_type:
- HeaderDef
---

# CONSOLE\_CURSOR\_INFO structure


Contains information about the console cursor.

Syntax
------

```ManagedCPlusPlus
typedef struct _CONSOLE_CURSOR_INFO {
  DWORD dwSize;
  BOOL  bVisible;
} CONSOLE_CURSOR_INFO, *PCONSOLE_CURSOR_INFO;
```

Members
-------

**dwSize**  
The percentage of the character cell that is filled by the cursor. This value is between 1 and 100. The cursor appearance varies, ranging from completely filling the cell to showing up as a horizontal line at the bottom of the cell.

**Note**  While the **dwSize** value is normally between 1 and 100, under some circumstances a value outside of that range might be returned. For example, if **CursorSize** is set to 0 in the registry, the **dwSize** value returned would be 0.

 

**bVisible**  
The visibility of the cursor. If the cursor is visible, this member is **TRUE**.

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


[**GetConsoleCursorInfo**](getconsolecursorinfo.md)

[**SetConsoleCursorInfo**](setconsolecursorinfo.md)

 

 




