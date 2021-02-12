---
title: SetConsoleOutputCP function
description: Sets the output code page used by the console associated with the calling process.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi2/SetConsoleOutputCP
- wincon/SetConsoleOutputCP
- SetConsoleOutputCP
MS-HAID:
- '\_win32\_setconsoleoutputcp'
- 'base.setconsoleoutputcp'
- 'consoles.setconsoleoutputcp'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 0b41e66b-ca19-4d69-9f39-92da158344ef

topic_type:
- apiref
api_name:
- SetConsoleOutputCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
---

# SetConsoleOutputCP function

Sets the output code page used by the console associated with the calling process. A console uses its output code page to translate the character values written by the various output functions into the images displayed in the console window.

## Syntax

```C
BOOL WINAPI SetConsoleOutputCP(
  _In_ UINT wCodePageID
);
```

## Parameters

*wCodePageID* \[in\]  
The identifier of the code page to set. For more information, see Remarks.

## Return value

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## Remarks

A code page maps 256 character codes to individual characters. Different code pages include different special characters, typically customized for a language or a group of languages.

If the current font is a fixed-pitch Unicode font, **SetConsoleOutputCP** changes the mapping of the character values into the glyph set of the font, rather than loading a separate font each time it is called. This affects how extended characters (ASCII value greater than 127) are displayed in a console window. However, if the current font is a raster font, **SetConsoleOutputCP** does not affect how extended characters are displayed.

To find the code pages that are installed or supported by the operating system, use the [EnumSystemCodePages](/windows/win32/api/winnls/nf-winnls-enumsystemcodepagesa) function. The identifiers of the code pages available on the local computer are also stored in the registry under the following key:

`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`

However, it is better to use [EnumSystemCodePages](/windows/win32/api/winnls/nf-winnls-enumsystemcodepagesa) to enumerate code pages because the registry can differ in different versions of Windows.
To determine whether a particular code page is valid, use the [IsValidCodePage](/windows/win32/api/winnls/nf-winnls-isvalidcodepage) function. To retrieve more information about a code page, including its name, use the [**GetCPInfoEx**](/windows/win32/api/winnls/nf-winnls-getcpinfoexa) function. For a list of available code page identifiers, see [Code Page Identifiers](/windows/win32/intl/code-page-identifiers).

To determine a console's current output code page, use the [**GetConsoleOutputCP**](getconsoleoutputcp.md) function. To set and retrieve a console's input code page, use the [**SetConsoleCP**](setconsolecp.md) and [**GetConsoleCP**](getconsolecp.md) functions.

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows 2000 Professional \[desktop apps only\] |
| Minimum supported server | Windows 2000 Server \[desktop apps only\] |
| Header | ConsoleApi2.h (via WinCon.h, include Windows.h) |
| Library | Kernel32.lib |
| DLL | Kernel32.dll |

## See also

[Console Code Pages](console-code-pages.md)

[Console Functions](console-functions.md)

[**GetConsoleCP**](getconsolecp.md)

[**GetConsoleOutputCP**](getconsoleoutputcp.md)

[**SetConsoleCP**](setconsolecp.md)