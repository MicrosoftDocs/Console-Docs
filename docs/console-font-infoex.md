---
title: CONSOLE_FONT_INFOEX structure
description: See reference information about the CONSOLE_FONT_INFOEX structure, which contains extended information for a console font.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords: 
- consoleapi3/CONSOLE_FONT_INFOEX
- wincon/CONSOLE_FONT_INFOEX
- CONSOLE_FONT_INFOEX
- consoleapi3/PCONSOLE_FONT_INFOEX
- wincon/PCONSOLE_FONT_INFOEX
- PCONSOLE_FONT_INFOEX
MS-HAID:
- 'base.CONSOLE\_FONT\_INFOEX'
- 'consoles.CONSOLE\_FONT\_INFOEX'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: e9a087e1-264d-4d48-8adb-771a0e35b511

topic_type:
- apiref
api_name:
- CONSOLE_FONT_INFOEX
api_location:
- WinCon.h
api_type:
- HeaderDef
---

# ``CONSOLE\_FONT\_INFOEX`` structure

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Contains extended information for a console font.

## Syntax

```C
typedef struct _CONSOLE_FONT_INFOEX {
  ULONG cbSize;
  DWORD nFont;
  COORD dwFontSize;
  UINT  FontFamily;
  UINT  FontWeight;
  WCHAR FaceName[LF_FACESIZE];
} CONSOLE_FONT_INFOEX, *PCONSOLE_FONT_INFOEX;
```

## Members

`cbSize`  
The size of this structure, in bytes. This member must be set to `sizeof(CONSOLE_FONT_INFOEX)` before calling [`GetCurrentConsoleFontEx`](getcurrentconsolefontex.md) or it will fail.

`nFont`  
The index of the font in the system's console font table.

`dwFontSize`  
A [`COORD`](coord-str.md) structure that contains the width and height of each character in the font, in logical units. The `X` member contains the width, while the `Y` member contains the height.

`FontFamily`  
The font pitch and family. For information about the possible values for this member, see the description of the `tmPitchAndFamily` member of the [`TEXTMETRIC`](https://msdn.microsoft.com/library/windows/desktop/dd145132) structure.

`FontWeight`  
The font weight. The weight can range from 100 to 1000, in multiples of 100. For example, the normal weight is 400, while 700 is bold.

`FaceName`  
The name of the typeface (such as Courier or Arial).

## Remarks

To obtain the size of the font, pass the font index to the [`GetConsoleFontSize`](getconsolefontsize.md) function.

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows Vista \[desktop apps only\] |
| Minimum supported server | Windows Server 2008 \[desktop apps only\] |
| Header | WinCon.h (include Windows.h) |

## See also

[`GetCurrentConsoleFontEx`](getcurrentconsolefontex.md)
