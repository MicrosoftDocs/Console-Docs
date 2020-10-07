---
title: GetConsoleTitle function
description: Retrieves the title and size of the title for the current console window.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi2/GetConsoleTitle
- wincon/GetConsoleTitle
- GetConsoleTitle
- consoleapi2/GetConsoleTitleA
- wincon/GetConsoleTitleA
- GetConsoleTitleA
- consoleapi2/GetConsoleTitleW
- wincon/GetConsoleTitleW
- GetConsoleTitleW
MS-HAID:
- '\_win32\_getconsoletitle'
- 'base.getconsoletitle'
- 'consoles.getconsoletitle'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: c58bba36-9813-4bdc-83bf-30d55f8d7d79

topic_type:
- apiref
api_name:
- GetConsoleTitle
- GetConsoleTitleA
- GetConsoleTitleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- API-Ms-Win-Core-Console-Ansi-L2-1-0.dll
- Kernel32Legacy.dll
api_type:
- DllExport
---

# GetConsoleTitle function

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Retrieves the title for the current console window.

## Syntax

```C
DWORD WINAPI GetConsoleTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

## Parameters

*lpConsoleTitle* \[out\]  
A pointer to a buffer that receives a null-terminated string containing the title. If the buffer is too small to store the title, the function stores as many characters of the title as will fit in the buffer, ending with a null terminator.

*nSize* \[in\]  
The size of the buffer pointed to by the *lpConsoleTitle* parameter, in characters.

## Return value

If the function succeeds, the return value is the length of the console window's title, in characters.

If the function fails, the return value is zero and [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) returns the error code.

## Remarks

To set the title for a console window, use the [**SetConsoleTitle**](setconsoletitle.md) function. To retrieve the original title string, use the [**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md) function.

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent. This decision intentionally aligns the Windows platform with other operating systems. Applications remoting via cross-platform utilities and transports like SSH may not work as expected if using this API.

## Examples

For an example, see [**SetConsoleTitle**](setconsoletitle.md).

## Requirements

| | |
|-|-|
| Minimum supported client | Windows 2000 Professional \[desktop apps only\] |
| Minimum supported server | Windows 2000 Server \[desktop apps only\] |
| Header | ConsoleApi2.h (via WinCon.h, include Windows.h) |
| Library | Kernel32.lib |
| DLL | Kernel32.dll |
| Unicode and ANSI names | **GetConsoleTitleW** (Unicode) and **GetConsoleTitleA** (ANSI) |

## See also

[Console Functions](console-functions.md)

[**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**SetConsoleTitle**](setconsoletitle.md)
