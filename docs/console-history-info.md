---
title: CONSOLE_HISTORY_INFO structure
description: Contains information about the console history.
author: bitcrazed
ms.author: richturn
ms.topic: article
ms.prod: console
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- 'base.console\_history\_info'
- 'consoles.console\_history\_info'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: df7d2f12-5299-47ed-b1f6-2db903dba81b

topic_type:
- apiref
api_name:
- CONSOLE_HISTORY_INFO
api_location:
- Wincon.h
api_type:
- HeaderDef
---

# CONSOLE\_HISTORY\_INFO structure


Contains information about the console history.

Syntax
------

```C
typedef struct {
  UINT  cbSize;
  UINT  HistoryBufferSize;
  UINT  NumberOfHistoryBuffers;
  DWORD dwFlags;
} CONSOLE_HISTORY_INFO, *PCONSOLE_HISTORY_INFO;
```

Members
-------

**cbSize**  
The size of the structure, in bytes. Set this member to `sizeof(CONSOLE_HISTORY_INFO)`.

**HistoryBufferSize**  
The number of commands kept in each history buffer.

**NumberOfHistoryBuffers**  
The number of history buffers kept for this console process.

**dwFlags**  
This parameter can be zero or the following value.

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
<td><span id="HISTORY_NO_DUP_FLAG"></span><span id="history_no_dup_flag"></span>
<strong>HISTORY_NO_DUP_FLAG</strong>
0x1</td>
<td><p>Duplicate entries will not be stored in the history buffer.</p></td>
</tr>
</tbody>
</table>

 

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
<td>Wincon.h</td>
</tr>
</tbody>
</table>

## <span id="see_also"></span>See also


[**GetConsoleHistoryInfo**](getconsolehistoryinfo.md)

[**SetConsoleHistoryInfo**](setconsolehistoryinfo.md)

 

 




