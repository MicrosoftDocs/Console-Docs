---
title: GetConsoleAliasesLength function
description: Retrieves the required size for the buffer used by the GetConsoleAliases function.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi3/GetConsoleAliasesLength
- wincon/GetConsoleAliasesLength
- GetConsoleAliasesLength
- consoleapi3/GetConsoleAliasesLengthA
- wincon/GetConsoleAliasesLengthA
- GetConsoleAliasesLengthA
- consoleapi3/GetConsoleAliasesLengthW
- wincon/GetConsoleAliasesLengthW
- GetConsoleAliasesLengthW
MS-HAID:
- 'base.getconsolealiaseslength'
- 'consoles.getconsolealiaseslength'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 29e49eba-0864-4ed7-af82-1ba639261c40

topic_type:
- apiref
api_name:
- GetConsoleAliasesLength
- GetConsoleAliasesLengthA
- GetConsoleAliasesLengthW
api_location:
- Kernel32.dll
api_type:
- DllExport
---

# GetConsoleAliasesLength function

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Retrieves the required size for the buffer used by the [**GetConsoleAliases**](getconsolealiases.md) function.

## Syntax

```C
DWORD WINAPI GetConsoleAliasesLength(
  _In_ LPTSTR lpExeName
);
```

## Parameters

*lpExeName* \[in\]  
The name of the executable file whose console aliases are to be retrieved.

## Return value

The size of the buffer required to store all console aliases defined for this executable file, in bytes.

## Remarks

To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later. For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows 2000 Professional \[desktop apps only\] |
| Minimum supported server | Windows 2000 Server \[desktop apps only\] |
| Header | ConsoleApi3.h (via WinCon.h, include Windows.h) |
| Library | Kernel32.lib |
| DLL | Kernel32.dll |
| Unicode and ANSI names | **GetConsoleAliasesLengthW** (Unicode) and **GetConsoleAliasesLengthA** (ANSI) |

## See also

[**AddConsoleAlias**](addconsolealias.md)

[Console Aliases](console-aliases.md)

[Console Functions](console-functions.md)

[**GetConsoleAlias**](getconsolealias.md)

[**GetConsoleAliases**](getconsolealiases.md)

[**GetConsoleAliasExes**](getconsolealiasexes.md)
