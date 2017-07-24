---
title: WINDOW\_BUFFER\_SIZE\_RECORD structure
description: Describes a change in the size of the console screen buffer.
author: bitcrazed
ms.author: richturn
ms.topic: article
ms.prod: console
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- '\_win32\_window\_buffer\_size\_record\_str'
- 'base.window\_buffer\_size\_record\_str'
- 'consoles.window\_buffer\_size\_record\_str'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 2f2875e8-aa09-455b-a923-7cc388525b98

topic_type:
- apiref
api_name:
- WINDOW_BUFFER_SIZE_RECORD
api_location:
- Wincon.h
api_type:
- HeaderDef
---

# WINDOW\_BUFFER\_SIZE\_RECORD structure


Describes a change in the size of the console screen buffer.

Syntax
------

```ManagedCPlusPlus
typedef struct _WINDOW_BUFFER_SIZE_RECORD {
  COORD dwSize;
} WINDOW_BUFFER_SIZE_RECORD;
```

Members
-------

**dwSize**  
A [**COORD**](coord-str.md) structure that contains the size of the console screen buffer, in character cell columns and rows.

Remarks
-------

Buffer size events are placed in the input buffer when the console is in window-aware mode (**ENABLE\_WINDOW\_INPUT**).

Examples
--------

For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).

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


[**COORD**](coord-str.md)

[**INPUT\_RECORD**](input-record-str.md)

[**ReadConsoleInput**](readconsoleinput.md)

 

 




