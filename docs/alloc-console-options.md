---
title: ALLOC_CONSOLE_OPTIONS structure
description: See reference information about the ALLOC_CONSOLE_OPTIONS structure, which contains extended information about a console screen buffer.
author: lhecker
ms.author: lhecker
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi/ALLOC_CONSOLE_OPTIONS
- ALLOC_CONSOLE_OPTIONS
- PALLOC_CONSOLE_OPTIONS
topic_type:
- apiref
api_name:
- ALLOC_CONSOLE_OPTIONS
api_location:
- WinCon.h
api_type:
- HeaderDef
---

# ALLOC\_CONSOLE\_OPTIONS structure

Controls how **AllocConsoleWithOptions** allocates a console window.

## Syntax

```C
typedef struct _ALLOC_CONSOLE_OPTIONS {
    ALLOC_CONSOLE_MODE mode;
    BOOL               useShowWindow;
    WORD               showWindow;
} ALLOC_CONSOLE_OPTIONS, *PALLOC_CONSOLE_OPTIONS;
```

## Members

**mode**  
This parameter can be one of the following values:

| Value | Meaning |
|-|-|
| **ALLOC\_CONSOLE\_MODE\_DEFAULT** 0 | Allocate a console session if one was requested by the parent process. |
| **ALLOC\_CONSOLE\_MODE\_NEW\_WINDOW** 1 | Allocate a console session with a window, even if this process was created with **CREATE\_NO\_CONSOLE** or **DETACHED\_PROCESS**. |
| **ALLOC\_CONSOLE\_MODE\_NO\_WINDOW** 2 | 	Allocate a console session without a window, even if this process was created with **CREATE\_NEW\_WINDOW** or **DETACHED\_PROCESS**. |

**useShowWindow**  
Specifies whether the **showWindow** parameter should be used.

**showWindow**  
If **useShowWindow** is **TRUE**, this specifies the **nCmdShow** used to show the console window. See [**ShowWindow**](/windows/win32/api/winuser/nf-winuser-showwindow) for more information.

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows 11 24H2 (build 26100) \[desktop apps only\] |
| Minimum supported server | n/a |
| Header | ConsoleApi.h (via WinCon.h, include Windows.h) |

## See also

[**AllocConsoleWithOptions**](allocconsolewithoptions.md)
