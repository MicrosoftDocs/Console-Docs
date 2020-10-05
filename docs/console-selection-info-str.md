---
title: CONSOLE_SELECTION_INFO structure
description: See reference information about the CONSOLE_SELECTION_INFO structure, which contains information for a console selection.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi3/CONSOLE_SELECTION_INFO
- wincon/CONSOLE_SELECTION_INFO
- CONSOLE_SELECTION_INFO
- consoleapi3/PCONSOLE_SELECTION_INFO
- wincon/PCONSOLE_SELECTION_INFO
- PCONSOLE_SELECTION_INFO
MS-HAID:
- '\_win32\_console\_selection\_info\_str'
- 'base.console\_selection\_info\_str'
- 'consoles.console\_selection\_info\_str'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 9530b249-8db4-4516-9cc8-2b452c6751f9

topic_type:
- apiref
api_name:
- CONSOLE_SELECTION_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
---

# CONSOLE\_SELECTION\_INFO structure

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Contains information for a console selection.

## Syntax

```C
typedef struct _CONSOLE_SELECTION_INFO {
  DWORD      dwFlags;
  COORD      dwSelectionAnchor;
  SMALL_RECT srSelection;
} CONSOLE_SELECTION_INFO, *PCONSOLE_SELECTION_INFO;
```

## Members

**dwFlags**  
The selection indicator. This member can be one or more of the following values.

| Value | Meaning |
|-|-|
| **CONSOLE_MOUSE_DOWN** 0x0008 | Mouse is down. The user is actively adjusting the selection rectangle with a mouse. |
| **CONSOLE_MOUSE_SELECTION** 0x0004 | Selecting with the mouse. If off, the user is operating `conhost.exe` mark mode selection with the keyboard. |
| **CONSOLE_NO_SELECTION** 0x0000 | No selection. |
| **CONSOLE_SELECTION_IN_PROGRESS** 0x0001 | Selection has begun. If a mouse selection, this will typically not occur without the `CONSOLE_SELECTION_NOT_EMPTY` flag. If a keyboard selection, this may occur when mark mode has been entered but the user is still navigating to the initial position. |
| **CONSOLE_SELECTION_NOT_EMPTY** 0x0002 | Selection rectangle not empty. The payload of *dwSelectionAnchor* and *srSelection* are valid.  |

**dwSelectionAnchor**  
A [**COORD**](coord-str.md) structure that specifies the selection anchor, in characters.

**srSelection**  
A [**SMALL\_RECT**](small-rect-str.md) structure that specifies the selection rectangle.

## Requirements

| | |
|-|-|
| Minimum supported client | Windows XP \[desktop apps only\] |
| Minimum supported server | Windows Server 2003 \[desktop apps only\] |
| Header | ConsoleApi3.h (via WinCon.h, include Windows.h) |

## See also

[**COORD**](coord-str.md)

[**GetConsoleSelectionInfo**](getconsoleselectioninfo.md)

[**SMALL\_RECT**](small-rect-str.md)
