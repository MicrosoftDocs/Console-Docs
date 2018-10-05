---
title: FOCUS_EVENT_RECORD structure
description: Describes a focus event in a console INPUT\_RECORD structure. These events are used internally and should be ignored.
author: bitcrazed
ms.author: richturn
ms.topic: article
ms.prod: console
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- '\_win32\_focus\_event\_record\_str'
- 'base.focus\_event\_record\_str'
- 'consoles.focus\_event\_record\_str'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 4db0ae89-8446-4f0a-98e2-ba0b11ef7efe

topic_type:
- apiref
api_name:
- FOCUS_EVENT_RECORD
api_location:
- Wincon.h
api_type:
- HeaderDef
---

# FOCUS\_EVENT\_RECORD structure


Describes a focus event in a console [**INPUT\_RECORD**](input-record-str.md) structure. These events are used internally and should be ignored.

Syntax
------

```C
typedef struct _FOCUS_EVENT_RECORD {
  BOOL bSetFocus;
} FOCUS_EVENT_RECORD;
```

Members
-------

**bSetFocus**  
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
<td>WinConTypes.h (via Wincon.h, include Windows.h)</td>
</tr>
</tbody>
</table>

## <span id="see_also"></span>See also


[**INPUT\_RECORD**](input-record-str.md)

 

 




