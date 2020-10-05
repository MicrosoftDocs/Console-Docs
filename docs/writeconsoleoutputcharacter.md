---
title: WriteConsoleOutputCharacter function
description: Copies a number of characters to consecutive cells of a console screen buffer, beginning at a specified location.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi2/WriteConsoleOutputCharacter
- wincon/WriteConsoleOutputCharacter
- WriteConsoleOutputCharacter
- consoleapi2/WriteConsoleOutputCharacterA
- wincon/WriteConsoleOutputCharacterA
- WriteConsoleOutputCharacterA
- consoleapi2/WriteConsoleOutputCharacterW
- wincon/WriteConsoleOutputCharacterW
- WriteConsoleOutputCharacterW
MS-HAID:
- '\_win32\_writeconsoleoutputcharacter'
- 'base.writeconsoleoutputcharacter'
- 'consoles.writeconsoleoutputcharacter'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 7cc935ea-6b19-4494-b746-259aa7aaa9cc
topic_type:
- apiref
api_name:
- WriteConsoleOutputCharacter
- WriteConsoleOutputCharacterA
- WriteConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
---

# WriteConsoleOutputCharacter function

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Copies a number of characters to consecutive cells of a console screen buffer, beginning at a specified location.

## Syntax

```C
BOOL WINAPI WriteConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _In_  LPCTSTR lpCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfCharsWritten
);
```

## Parameters

*hConsoleOutput* \[in\]  
A handle to the console screen buffer. The handle must have the **GENERIC\_WRITE** access right. For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).

*lpCharacter* \[in\]  
The characters to be written to the console screen buffer.

*nLength* \[in\]  
The number of characters to be written.

*dwWriteCoord* \[in\]  
A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell in the console screen buffer to which characters will be written.

*lpNumberOfCharsWritten* \[out\]  
A pointer to a variable that receives the number of characters actually written.

## Return value

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## Remarks

If the number of characters to be written to extends beyond the end of the specified row in the console screen buffer, characters are written to the next row. If the number of characters to be written to extends beyond the end of the console screen buffer, characters are written up to the end of the console screen buffer.

The attribute values at the positions written to are not changed.

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

## Requirements

| | |
|-|-|
| Minimum supported client | Windows 2000 Professional \[desktop apps only\] |
| Minimum supported server | Windows 2000 Server \[desktop apps only\] |
| Header | ConsoleApi2.h (via WinCon.h, include Windows.h) |
| Library | Kernel32.lib |
| DLL | Kernel32.dll |
| Unicode and ANSI names | **WriteConsoleOutputCharacterW** (Unicode) and **WriteConsoleOutputCharacterA** (ANSI) |

## See also

[Console Functions](console-functions.md)

[**COORD**](coord-str.md)

[Low-Level Console Output Functions](low-level-console-output-functions.md)

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md)

[**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)

[**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md)
