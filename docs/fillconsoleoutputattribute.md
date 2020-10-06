---
title: FillConsoleOutputAttribute function
description: Sets the character attributes for a specified number of character cells, beginning at the specified coordinates in a screen buffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi2/FillConsoleOutputAttribute
- wincon/FillConsoleOutputAttribute
- FillConsoleOutputAttribute
MS-HAID:
- '\_win32\_fillconsoleoutputattribute'
- 'base.fillconsoleoutputattribute'
- 'consoles.fillconsoleoutputattribute'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 09440263-71c4-4b7a-8fc6-a2b4fcd677ff

topic_type:
- apiref
api_name:
- FillConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
---

# FillConsoleOutputAttribute function

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Sets the character attributes for a specified number of character cells, beginning at the specified coordinates in a screen buffer.

## Syntax

```C
BOOL WINAPI FillConsoleOutputAttribute(
  _In_  HANDLE  hConsoleOutput,
  _In_  WORD    wAttribute,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfAttrsWritten
);
```

## Parameters

*hConsoleOutput* \[in\]  
A handle to the console screen buffer. The handle must have the **GENERIC\_WRITE** access right. For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).

*wAttribute* \[in\]  
The attributes to use when writing to the console screen buffer. For more information, see [Character Attributes](console-screen-buffers.md#character-attributes).

*nLength* \[in\]  
The number of character cells to be set to the specified color attributes.

*dwWriteCoord* \[in\]  
A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell whose attributes are to be set.

*lpNumberOfAttrsWritten* \[out\]  
A pointer to a variable that receives the number of character cells whose attributes were actually set.

## Return value

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## Remarks

If the number of character cells whose attributes are to be set extends beyond the end of the specified row in the console screen buffer, the cells of the next row are set. If the number of cells to write to extends beyond the end of the console screen buffer, the cells are written up to the end of the console screen buffer.

The character values at the positions written to are not changed.

> [!TIP]
> This API is not recommended and does not have a specific **[virtual terminal](console-virtual-terminal-sequences)** equivalent. Filling the region outside the viewable window is not supported and is reserved for the terminal's history space. Filling a visible region with new text or color is performed through **[moving the cursor](console-virtual-terminal-sequences#cursor-positioning)**, **[setting the new attributes](console-virtual-terminal-sequences#text-formatting)**, then writing the desired text for that region, repeating characters if necessary for the length of the fill run. Additional cursor movement may be required followed by writing the desired text to fill a rectangular region. More information can be found in **[classic console versus virtual terminal](classic-vs-vt.md)** documentation.

## Requirements

| | |
|-|-|
| Minimum supported client | Windows 2000 Professional \[desktop apps only\] |
| Minimum supported server | Windows 2000 Server \[desktop apps only\] |
| Header | ConsoleApi2.h (via WinCon.h, include Windows.h) |
| Library | Kernel32.lib |
| DLL | Kernel32.dll |

## See also

[Console Functions](console-functions.md)

[**COORD**](coord-str.md)

[**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md)

[Low-Level Console Output Functions](low-level-console-output-functions.md)

[**SetConsoleTextAttribute**](setconsoletextattribute.md)

[**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md)
