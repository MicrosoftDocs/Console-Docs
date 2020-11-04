---
title: CONSOLE_CURSOR_INFO structure
description: Contains the size and visibility information about the about the console cursor.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords: 
- wincontypes/CONSOLE_CURSOR_INFO
- wincon/CONSOLE_CURSOR_INFO
- CONSOLE_CURSOR_INFO
- wincontypes/PCONSOLE_CURSOR_INFO
- wincon/PCONSOLE_CURSOR_INFO
- PCONSOLE_CURSOR_INFO
MS-HAID:
- '_win32_console_cursor_info_str`
- 'base.console_cursor_info_str'
- 'consoles.console_cursor_info_str'

MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 0e71ce8c-e008-4bd7-922e-c44484b425ef

topic_type:
- apiref
api_name:
- CONSOLE_CURSOR_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
---

# `CONSOLE_CURSOR_INFO` structure

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Contains information about the console cursor.

## Syntax

```C
typedef struct _CONSOLE_CURSOR_INFO {
  DWORD dwSize;
  BOOL  bVisible;
} CONSOLE_CURSOR_INFO, *PCONSOLE_CURSOR_INFO;
```

## Members

`dwSize`  
The percentage of the character cell that is filled by the cursor. This value is between 1 and 100. The cursor appearance varies, ranging from completely filling the cell to showing up as a horizontal line at the bottom of the cell.

> [!NOTE]
>While the `dwSize` value is normally between 1 and 100, under some circumstances a value outside of that range might be returned. For example, if `CursorSize` is set to 0 in the registry, the `dwSize` value returned would be 0.

 `bVisible`  
The visibility of the cursor. If the cursor is visible, this member is `TRUE`.

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows 2000 Professional \[desktop apps only\] |
| Minimum supported server | Windows 2000 Server \[desktop apps only\] |
| Header | WinCon.h (include Windows.h) |

## See also

[`GetConsoleCursorInfo`](getconsolecursorinfo.md)

[`SetConsoleCursorInfo`](setconsolecursorinfo.md)
