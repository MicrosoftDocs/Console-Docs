---
title: WriteConsoleOutputAttribute function
description: Copies a number of character attributes to consecutive cells of a console screen buffer, beginning at a specified location.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi2/WriteConsoleOutputAttribute
- wincon/WriteConsoleOutputAttribute
- WriteConsoleOutputAttribute
MS-HAID:
- '\_win32\_writeconsoleoutputattribute'
- 'base.writeconsoleoutputattribute'
- 'consoles.writeconsoleoutputattribute'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 52a9d6e5-072e-4411-9945-10bd3dd61e25

topic_type:
- apiref
api_name:
- WriteConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
---

# WriteConsoleOutputAttribute function

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Copies a number of character attributes to consecutive cells of a console screen buffer, beginning at a specified location.

## Syntax

```C
BOOL WINAPI WriteConsoleOutputAttribute(
  _In_        HANDLE  hConsoleOutput,
  _In_  const WORD    *lpAttribute,
  _In_        DWORD   nLength,
  _In_        COORD   dwWriteCoord,
  _Out_       LPDWORD lpNumberOfAttrsWritten
);
```

## Parameters

*hConsoleOutput* \[in\]  
A handle to the console screen buffer. The handle must have the **GENERIC\_WRITE** access right. For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).

*lpAttribute* \[in\]  
The attributes to be used when writing to the console screen buffer. For more information, see [Character Attributes](console-screen-buffers.md#character-attributes).

*nLength* \[in\]  
The number of screen buffer character cells to which the attributes will be copied.

*dwWriteCoord* \[in\]  
A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell in the console screen buffer to which the attributes will be written.

*lpNumberOfAttrsWritten* \[out\]  
A pointer to a variable that receives the number of attributes actually written to the console screen buffer.

## Return value

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## Remarks

If the number of attributes to be written to extends beyond the end of the specified row in the console screen buffer, attributes are written to the next row. If the number of attributes to be written to extends beyond the end of the console screen buffer, the attributes are written up to the end of the console screen buffer.

The character values at the positions written to are not changed.

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

[Low-Level Console Output Functions](low-level-console-output-functions.md)

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md)

[**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)

[**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)
