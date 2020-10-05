---
title: FOCUS_EVENT_RECORD structure
description: Describes a focus event in a console INPUT\_RECORD structure. These events are used internally and should be ignored.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- wincontypes/FOCUS_EVENT_RECORD
- wincon/FOCUS_EVENT_RECORD
- FOCUS_EVENT_RECORD
- wincontypes/PFOCUS_EVENT_RECORD
- wincon/PFOCUS_EVENT_RECORD
- PFOCUS_EVENT_RECORD
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
- WinCon.h
api_type:
- HeaderDef
---

# FOCUS\_EVENT\_RECORD structure

Describes a focus event in a console [**INPUT\_RECORD**](input-record-str.md) structure. These events are used internally and should be ignored.

## Syntax

```C
typedef struct _FOCUS_EVENT_RECORD {
  BOOL bSetFocus;
} FOCUS_EVENT_RECORD;
```

## Members

**bSetFocus**  
Reserved.

## Requirements

| | |
|-|-|
| Minimum supported client | Windows 2000 Professional \[desktop apps only\] |
| Minimum supported server | Windows 2000 Server \[desktop apps only\] |
| Header | WinConTypes.h (via WinCon.h, include Windows.h) |

## See also

[**INPUT\_RECORD**](input-record-str.md)
