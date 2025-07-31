---
title: CONSOLE_FONT_INFO structure
description: See reference information about the CONSOLE_FONT_INFO structure, which contains the index and size for a console font.
author: miniksa
ms.author: miniksa
ms.topic: reference
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords: 
- wincontypes/CONSOLE_FONT_INFO
- wincon/CONSOLE_FONT_INFO
- CONSOLE_FONT_INFO
- wincontypes/PCONSOLE_FONT_INFO
- wincon/PCONSOLE_FONT_INFO
- PCONSOLE_FONT_INFO
MS-HAID:
- '\_win32\_console\_font\_info\_str'
- 'base.console\_font\_info\_str'
- 'consoles.console\_font\_info\_str'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 380b8183-1964-46f2-a511-01f39f21f5c5
topic_type:
- apiref
api_name:
- CONSOLE_FONT_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
---

# CONSOLE\_FONT\_INFO structure

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Contains information for a console font.

## Syntax

```C
typedef struct _CONSOLE_FONT_INFO {
  DWORD nFont;
  COORD dwFontSize;
} CONSOLE_FONT_INFO, *PCONSOLE_FONT_INFO;
```

## Members

**nFont**  
The index of the font in the system's console font table.

**dwFontSize**  
A [**COORD**](coord-str.md) structure that contains the width and height of each character in the font, in logical units. The **X** member contains the width, while the **Y** member contains the height.

## Remarks

To obtain the size of the font, pass the font index to the [**GetConsoleFontSize**](getconsolefontsize.md) function.

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows XP \[desktop apps only\] |
| Minimum supported server | Windows Server 2003 \[desktop apps only\] |
| Header | WinCon.h (include Windows.h) |

## See also

[**COORD**](coord-str.md)

[**GetCurrentConsoleFont**](getcurrentconsolefont.md)
