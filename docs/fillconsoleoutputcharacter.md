---
title: FillConsoleOutputCharacter function
description: Writes a character to the console screen buffer a specified number of times, beginning at the specified coordinates.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi2/FillConsoleOutputCharacter
- wincon/FillConsoleOutputCharacter
- FillConsoleOutputCharacter
- consoleapi2/FillConsoleOutputCharacterA
- wincon/FillConsoleOutputCharacterA
- FillConsoleOutputCharacterA
- consoleapi2/FillConsoleOutputCharacterW
- wincon/FillConsoleOutputCharacterW
- FillConsoleOutputCharacterW
MS-HAID:
- '_win32_fillconsoleoutputcharacter'
- 'base.fillconsoleoutputcharacter'
- 'consoles.fillconsoleoutputcharacter'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 37579cc9-14b3-4fd9-81ed-abaad5c7bd1a

topic_type:
- apiref
api_name:
- FillConsoleOutputCharacter
- FillConsoleOutputCharacterA
- FillConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
---

# FillConsoleOutputCharacter function

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Writes a character to the console screen buffer a specified number of times, beginning at the specified coordinates.

## Syntax

```C
BOOL WINAPI FillConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _In_  TCHAR   cCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfCharsWritten
);
```

## Parameters

*hConsoleOutput* \[in\]  
A handle to the console screen buffer. The handle must have the `GENERIC_WRITE` access right. For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).

*cCharacter* \[in\]  
The character to be written to the console screen buffer.

*nLength* \[in\]  
The number of character cells to which the character should be written.

*dwWriteCoord* \[in\]  
A [`COORD`](coord-str.md) structure that specifies the character coordinates of the first cell to which the character is to be written.

*lpNumberOfCharsWritten* \[out\]  
A pointer to a variable that receives the number of characters actually written to the console screen buffer.

## Return value

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [`GetLastError`](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## Remarks

If the number of characters to write to extends beyond the end of the specified row in the console screen buffer, characters are written to the next row. If the number of characters to write to extends beyond the end of the console screen buffer, the characters are written up to the end of the console screen buffer.

The attribute values at the positions written are not changed.

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> This API is not recommended and does not have a specific `[virtual terminal](console-virtual-terminal-sequences.md)` equivalent. Filling the region outside the viewable window is not supported and is reserved for the terminal's history space. Filling a visible region with new text or color is performed through `[moving the cursor](console-virtual-terminal-sequences.md#cursor-positioning)`, `[setting the new attributes](console-virtual-terminal-sequences.md#text-formatting)`, then writing the desired text for that region, repeating characters if necessary for the length of the fill run. Additional cursor movement may be required followed by writing the desired text to fill a rectangular region. The client application is expected to keep its own memory of what is on the screen and is not able to query the remote state. More information can be found in `[classic console versus virtual terminal](classic-vs-vt.md)` documentation.

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows 2000 Professional \[desktop apps only\] |
| Minimum supported server | Windows 2000 Server \[desktop apps only\] |
| Header | ConsoleApi2.h (via WinCon.h, include Windows.h) |
| Library | Kernel32.lib |
| DLL | Kernel32.dll |
| Unicode and ANSI names | `FillConsoleOutputCharacterW` (Unicode) and `FillConsoleOutputCharacterA` (ANSI) |

## See also

[Console Functions](console-functions.md)

[`COORD`](coord-str.md)

[`FillConsoleOutputAttribute`](fillconsoleoutputattribute.md)

[Low-Level Console Output Functions](low-level-console-output-functions.md)

[`SetConsoleCP`](setconsolecp.md)

[`SetConsoleOutputCP`](setconsoleoutputcp.md)

[`WriteConsoleOutputCharacter`](writeconsoleoutputcharacter.md)
