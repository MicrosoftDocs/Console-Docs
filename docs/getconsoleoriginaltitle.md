---
title: GetConsoleOriginalTitle function
description: See reference information about the GetConsoleOriginalTitle function, which retrieves the original title for the current console window.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi2/GetConsoleOriginalTitle
- wincon/GetConsoleOriginalTitle
- GetConsoleOriginalTitle
- consoleapi2/GetConsoleOriginalTitleA
- wincon/GetConsoleOriginalTitleA
- GetConsoleOriginalTitleA
- consoleapi2/GetConsoleOriginalTitleW
- wincon/GetConsoleOriginalTitleW
- GetConsoleOriginalTitleW
MS-HAID:
- 'base.getconsoleoriginaltitle'
- 'consoles.getconsoleoriginaltitle'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: e3dd02f4-4899-4df0-a960-3b2625c15fee

topic_type:
- apiref
api_name:
- GetConsoleOriginalTitle
- GetConsoleOriginalTitleA
- GetConsoleOriginalTitleW
api_location:
- Kernel32.dll
api_type:
- DllExport
---

# GetConsoleOriginalTitle function

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Retrieves the original title for the current console window.

## Syntax

```C
DWORD WINAPI GetConsoleOriginalTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

## Parameters

*lpConsoleTitle* \[out\]  
A pointer to a buffer that receives a null-terminated string containing the original title.

*nSize* \[in\]  
The size of the *lpConsoleTitle* buffer, in characters.

## Return value

If *nSize* is zero, the return value is zero.

If the function succeeds, the return value is the length of the original console title, in characters.

If the function fails, the return value is zero and [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) returns the error code.

## Remarks

To set the title for a console window, use the [**SetConsoleTitle**](setconsoletitle.md) function. To retrieve the current title string, use the [**GetConsoleTitle**](getconsoletitle.md) function.

To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0600 or later. For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).

> [!TIP]
> This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent. This decision intentionally aligns the Windows platform with other operating systems. Applications remoting via cross-platform utilities and transports like SSH may not work as expected if using this API.

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows Vista \[desktop apps only\] |
| Minimum supported server | Windows Server 2008 \[desktop apps only\] |
| Header | ConsoleApi2.h (via WinCon.h, include Windows.h) |
| Library | Kernel32.lib |
| DLL | Kernel32.dll |
| Unicode and ANSI names | **GetConsoleOriginalTitleW** (Unicode) and **GetConsoleOriginalTitleA** (ANSI) |

## See also

[Console Functions](console-functions.md)

[**GetConsoleTitle**](getconsoletitle.md)

[**SetConsoleTitle**](setconsoletitle.md)
