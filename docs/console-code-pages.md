---
title: Console Code Pages
description: A code page is a mapping of 256 character codes to individual characters. Different code pages include different special characters, typically customized for a language or a group of languages.
author: miniksa
ms.author: miniksa
ms.topic: reference
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- '\_win32\_console\_code\_pages'
- 'base.console\_code\_pages'
- 'consoles.console\_code\_pages'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 98d56bb1-83d2-40aa-adac-fc2e8beab337
---

# Console Code Pages

A *code page* is a mapping of 256 character codes to individual characters. Different code pages include different special characters, typically customized for a language or a group of languages.

Associated with each console are two code pages: one for input and one for output. A console uses its input code page to translate keyboard input into the corresponding character value. It uses its output code page to translate the character values written by the various output functions into the images displayed in the console window. An application can use the [**SetConsoleCP**](setconsolecp.md) and [**GetConsoleCP**](getconsolecp.md) functions to set and retrieve a console's input code pages and the [**SetConsoleOutputCP**](setconsoleoutputcp.md) and [**GetConsoleOutputCP**](getconsoleoutputcp.md) functions to set and retrieve its output code pages.

The identifiers of the code pages available on the local computer are stored in the registry under the following key:
`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`

For information about using the registry functions to determine the available code pages, see [**Registry**](/windows/win32/sysinfo/registry).

> [!TIP]
> It is recommended for all new and updated command-line applications to avoid code pages and use **[Unicode](/windows/win32/intl/unicode)**. UTF-16 formatted text can be sent to the *W* family of console APIs. UTF-8 formatted text can be sent to the *A* family of console APIs after ensuring the code page is first set to **[65001 (CP_UTF8)](/windows/win32/intl/code-page-identifiers)** with the [**SetConsoleCP**](setconsolecp.md) and [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions.
