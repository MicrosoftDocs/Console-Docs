---
title: CONSOLE_HISTORY_INFO structure
description: See reference information about the CONSOLE_HISTORY_INFO structure, which contains information about the console history.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords: 
- consoleapi3/CONSOLE_HISTORY_INFO
- wincon/CONSOLE_HISTORY_INFO
- CONSOLE_HISTORY_INFO
- consoleapi3/PCONSOLE_HISTORY_INFO
- wincon/PCONSOLE_HISTORY_INFO
- PCONSOLE_HISTORY_INFO
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
- WinCon.h
api_type:
- HeaderDef
---

# CONSOLE\_HISTORY\_INFO structure

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Contains information about the console history.

## Syntax

```C
typedef struct {
  UINT  cbSize;
  UINT  HistoryBufferSize;
  UINT  NumberOfHistoryBuffers;
  DWORD dwFlags;
} CONSOLE_HISTORY_INFO, *PCONSOLE_HISTORY_INFO;
```

## Members

`cbSize`  
The size of the structure, in bytes. Set this member to `sizeof(CONSOLE_HISTORY_INFO)`.

`HistoryBufferSize`  
The number of commands kept in each history buffer.

`NumberOfHistoryBuffers`  
The number of history buffers kept for this console process.

`dwFlags`  
This parameter can be zero or the following value.

| Value | Meaning |
|-|-|
| `HISTORY_NO_DUP_FLAG` 0x1 | Duplicate entries will not be stored in the history buffer.

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows Vista \[desktop apps only\] |
| Minimum supported server | Windows Server 2008 \[desktop apps only\] |
| Header | ConsoleApi3.h (via WinCon.h, include Windows.h) |

## See also

[`GetConsoleHistoryInfo`](getconsolehistoryinfo.md)

[`SetConsoleHistoryInfo`](setconsolehistoryinfo.md)
