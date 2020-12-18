---
title: MENU_EVENT_RECORD structure
description: Describes a menu event in a console INPUT_RECORD structure. These events are used internally and should be ignored.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- wincontypes/MENU_EVENT_RECORD
- wincon/MENU_EVENT_RECORD
- MENU_EVENT_RECORD
- wincontypes/PMENU_EVENT_RECORD
- wincon/PMENU_EVENT_RECORD
- PMENU_EVENT_RECORD
MS-HAID:
- '_win32_menu_event_record_str'
- 'base.menu_event_record_str'
- 'consoles.menu_event_record_str'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 7efef0e0-01ba-44ba-a972-25c6b3aed2bd

topic_type:
- apiref
api_name:
- MENU_EVENT_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
---

# MENU_EVENT_RECORD structure

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Describes a menu event in a console [`INPUT_RECORD`](input-record-str.md) structure. These events are used internally and should be ignored.

## Syntax

```C
typedef struct _MENU_EVENT_RECORD {
  UINT dwCommandId;
} MENU_EVENT_RECORD, *PMENU_EVENT_RECORD;
```

## Members

`dwCommandId`  
Reserved.

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows 2000 Professional \[desktop apps only\] |
| Minimum supported server | Windows 2000 Server \[desktop apps only\] |
| Header | WinConTypes.h (via WinCon.h, include Windows.h) |

## See also

[`INPUT_RECORD`](input-record-str.md)
