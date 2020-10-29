---
title: CHAR_INFO structure
description: Specifies a Unicode or ANSI character and its attributes. This structure is used by console functions to read from and write to a console screen buffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords: 
- wincontypes/CHAR_INFO
- wincon/CHAR_INFO
- CHAR_INFO
- wincontypes/PCHAR_INFO
- wincon/PCHAR_INFO
- PCHAR_INFO
MS-HAID:
- '\_win32\_char\_info\_str'
- 'base.char\_info\_str'
- 'consoles.char\_info\_str'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 5574a862-b262-41af-8862-e9837c5c7b5f
topic_type:
- apiref
api_name:
- CHAR_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
---

# CHAR\_INFO structure

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Specifies a Unicode or ANSI character and its attributes. This structure is used by console functions to read from and write to a console screen buffer.

## Syntax

```C
typedef struct _CHAR_INFO {
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } Char;
  WORD  Attributes;
} CHAR_INFO, *PCHAR_INFO;
```

## Members

**Char**  
A union of the following members.

**UnicodeChar**  
Unicode character of a screen buffer character cell.

**AsciiChar**  
ANSI character of a screen buffer character cell.

**Attributes**  
The character attributes. This member can be zero or any combination of the following values.

| Value | Meaning |
|-|-|
| **FOREGROUND_BLUE** `0x0001` | Text color contains blue. |
| **FOREGROUND_GREEN** `0x0002` | Text color contains green. |
| **FOREGROUND_RED** `0x0004` | Text color contains red. |
| **FOREGROUND_INTENSITY** `0x0008` | Text color is intensified. |
| **BACKGROUND_BLUE** `0x0010` | Background color contains blue. |
| **BACKGROUND_GREEN** `0x0020` | Background color contains green. |
| **BACKGROUND_RED** `0x0040` | Background color contains red. |
| **BACKGROUND_INTENSITY** `0x0080` | Background color is intensified. |
| **COMMON_LVB_LEADING_BYTE** `0x0100` | Leading byte. |
| **COMMON_LVB_TRAILING_BYTE** `0x0200` | Trailing byte. |
| **COMMON_LVB_GRID_HORIZONTAL** `0x0400` | Top horizontal. |
| **COMMON_LVB_GRID_LVERTICAL** `0x0800` | Left vertical. |
| **COMMON_LVB_GRID_RVERTICAL** `0x1000` | Right vertical. |
| **COMMON_LVB_REVERSE_VIDEO** `0x4000` | Reverse foreground and background attribute. |
| **COMMON_LVB_UNDERSCORE** `0x8000` | Underscore. |

## Examples

For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows 2000 Professional \[desktop apps only\] |
| Minimum supported server | Windows 2000 Server \[desktop apps only\] |
| Header | WinCon.h (include Windows.h) |

## See also

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)
