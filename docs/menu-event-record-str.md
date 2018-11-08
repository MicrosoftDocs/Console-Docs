---
title: MENU_EVENT_RECORD structure
description: Describes a menu event in a console INPUT\_RECORD structure. These events are used internally and should be ignored.
author: bitcrazed
ms.author: richturn
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- '\_win32\_menu\_event\_record\_str'
- 'base.menu\_event\_record\_str'
- 'consoles.menu\_event\_record\_str'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 7efef0e0-01ba-44ba-a972-25c6b3aed2bd

topic_type:
- apiref
api_name:
- MENU_EVENT_RECORD
api_location:
- Wincon.h
api_type:
- HeaderDef
---

# MENU\_EVENT\_RECORD structure


Describes a menu event in a console [**INPUT\_RECORD**](input-record-str.md) structure. These events are used internally and should be ignored.

Syntax
------

```C
typedef struct _MENU_EVENT_RECORD {
  UINT dwCommandId;
} MENU_EVENT_RECORD, *PMENU_EVENT_RECORD;
```

Members
-------

**dwCommandId**  
Reserved.

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


[**INPUT\_RECORD**](input-record-str.md)

 

 




