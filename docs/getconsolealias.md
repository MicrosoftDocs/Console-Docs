---
title: GetConsoleAlias function
description: Retrieves the text for the specified console alias and the name of the executable.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi3/GetConsoleAlias
- wincon/GetConsoleAlias
- GetConsoleAlias
- consoleapi3/GetConsoleAliasA
- wincon/GetConsoleAliasA
- GetConsoleAliasA
- consoleapi3/GetConsoleAliasW
- wincon/GetConsoleAliasW
- GetConsoleAliasW
MS-HAID:
- 'base.getconsolealias'
- 'consoles.getconsolealias'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: e8514f24-8121-4fad-94bb-c9eedf7a700d

topic_type:
- apiref
api_name:
- GetConsoleAlias
- GetConsoleAliasA
- GetConsoleAliasW
api_location:
- Kernel32.dll
api_type:
- DllExport
---

# GetConsoleAlias function

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Retrieves the text for the specified console alias and executable.

## Syntax

```C
DWORD WINAPI GetConsoleAlias(
  _In_  LPTSTR lpSource,
  _Out_ LPTSTR lpTargetBuffer,
  _In_  DWORD  TargetBufferLength,
  _In_  LPTSTR lpExeName
);
```

## Parameters

*lpSource* \[in\]  
The console alias whose text is to be retrieved.

*lpTargetBuffer* \[out\]  
A pointer to a buffer that receives the text associated with the console alias.

*TargetBufferLength* \[in\]  
The size of the buffer pointed to by *lpTargetBuffer*, in bytes.

*lpExeName* \[in\]  
The name of the executable file.

## Return value

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [`GetLastError`](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## Remarks

To compile an application that uses this function, define `_WIN32_WINNT` as 0x0501 or later. For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows 2000 Professional \[desktop apps only\] |
| Minimum supported server | Windows 2000 Server \[desktop apps only\] |
| Header | ConsoleApi3.h (via WinCon.h, include Windows.h) |
| Library | Kernel32.lib |
| DLL | Kernel32.dll |
| Unicode and ANSI names | `GetConsoleAliasW` (Unicode) and `GetConsoleAliasA` (ANSI) |

## See also

[Console Aliases](console-aliases.md)

[Console Functions](console-functions.md)

[`AddConsoleAlias`](addconsolealias.md)

[`GetConsoleAliases`](getconsolealiases.md)

[`GetConsoleAliasExes`](getconsolealiasexes.md)
