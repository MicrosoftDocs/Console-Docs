---
title: WINDOW_BUFFER_SIZE_RECORD structure
description: See reference information about the WINDOW_BUFFER_SIZE_RECORD structure, which describes a change in the size of the console screen buffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- wincontypes/WINDOW_BUFFER_SIZE_RECORD
- wincon/WINDOW_BUFFER_SIZE_RECORD
- WINDOW_BUFFER_SIZE_RECORD
- wincontypes/PWINDOW_BUFFER_SIZE_RECORD
- wincon/PWINDOW_BUFFER_SIZE_RECORD
- PWINDOW_BUFFER_SIZE_RECORD
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
- WinCon.h
api_type:
- HeaderDef
---

# WINDOW\_BUFFER\_SIZE\_RECORD structure

Describes a change in the size of the console screen buffer.

## Syntax

```C
typedef struct _WINDOW_BUFFER_SIZE_RECORD {
  COORD dwSize;
} WINDOW_BUFFER_SIZE_RECORD;
```

## Members

**dwSize**  
A [**COORD**](coord-str.md) structure that contains the size of the console screen buffer, in character cell columns and rows.

## Remarks

Buffer size events are placed in the input buffer when the console is in window-aware mode (**ENABLE\_WINDOW\_INPUT**).

## Examples

For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows 2000 Professional \[desktop apps only\] |
| Minimum supported server | Windows 2000 Server \[desktop apps only\] |
| Header | WinConTypes.h (via WinCon.h, include Windows.h) |

## See also

[**COORD**](coord-str.md)

[**INPUT\_RECORD**](input-record-str.md)

[**ReadConsoleInput**](readconsoleinput.md)
