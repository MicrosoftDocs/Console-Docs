---
title: AddConsoleAlias function
description: See reference information about the AddConsoleAlias function, which defines a console alias for the specified executable.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords: 
- consoleapi3/AddConsoleAlias
- consoleapi3/AddConsoleAliasA
- consoleapi3/AddConsoleAliasW
- wincon/AddConsoleAlias
- wincon/AddConsoleAliasA
- wincon/AddConsoleAliasW
- AddConsoleAlias
- AddConsoleAliasA
- AddConsoleAliasW
MS-HAID:
- 'base.addconsolealias'
- 'consoles.addconsolealias'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: e4072c3c-cf32-4992-847e-efdb846e5784
topic_type:
- apiref
api_name:
- AddConsoleAlias
- AddConsoleAliasA
- AddConsoleAliasW
api_location:
- Kernel32.dll
api_type:
- DllExport
---

# AddConsoleAlias function

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Defines a console alias for the specified executable.

## Syntax

```C
BOOL WINAPI AddConsoleAlias(
  _In_ LPCTSTR Source,
  _In_ LPCTSTR Target,
  _In_ LPCTSTR ExeName
);
```

## Parameters

*Source* \[in\]  
The console alias to be mapped to the text specified by *Target*.

*Target* \[in\]  
The text to be substituted for *Source*. If this parameter is `NULL`, then the console alias is removed.

*ExeName* \[in\]  
The name of the executable file for which the console alias is to be defined.

## Return value

If the function succeeds, the return value is `TRUE`.

If the function fails, the return value is `FALSE`. To get extended error information, call [`GetLastError`](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## Remarks

To compile an application that uses this function, define `\_WIN32\_WINNT` as 0x0501 or later. For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## Examples

For an example, see [Console Aliases](console-aliases.md).

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows 2000 Professional \[desktop apps only\] |
| Minimum supported server | Windows 2000 Server \[desktop apps only\] |
| Header | ConsoleApi3.h (via WinCon.h, include Windows.h) |
| Library | Kernel32.lib |
| DLL | Kernel32.dll |
| Unicode and ANSI names | `AddConsoleAliasW` (Unicode) and `AddConsoleAliasA` (ANSI) |

## See also

[Console Aliases](console-aliases.md)

[Console Functions](console-functions.md)

[`GetConsoleAlias`](getconsolealias.md)

[`GetConsoleAliases`](getconsolealiases.md)

[`GetConsoleAliasExes`](getconsolealiasexes.md)
