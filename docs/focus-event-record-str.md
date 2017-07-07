---
title: FOCUS\_EVENT\_RECORD structure
description: Describes a focus event in a console INPUT\_RECORD structure. These events are used internally and should be ignored.
author: bitcrazed
ms.author: richturn
ms.topic: article
ms.prod: console
keywords: console, character mode applications, command line applications, terminal applications, console api
---

# FOCUS\_EVENT\_RECORD structure


Describes a focus event in a console [**INPUT\_RECORD**](input-record-str.md) structure. These events are used internally and should be ignored.

Syntax
------

```ManagedCPlusPlus
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
<td>Wincon.h (include Windows.h)</td>
</tr>
</tbody>
</table>

## <span id="see_also"></span>See also


[**INPUT\_RECORD**](input-record-str.md)

 

 




