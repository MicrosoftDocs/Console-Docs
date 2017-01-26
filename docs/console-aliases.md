---
title: Console Aliases
description: Console aliases are used to map source strings to target strings.
author: miniksa
ms.author: miniksa


MS-HAID:
- 'base.console\_aliases'
- 'consoles.console\_aliases'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 8169708b-83da-47ef-94be-eca3ca7d0a5b
---

# Console Aliases


Console aliases are used to map source strings to target strings. For example, you can define a console alias that maps "test" to "cd \\a\_very\_long\_path\\test". When you type "test" at the command line, the console subsystem expands the alias and executes the specified cd command.

To define a console alias, use Doskey.exe to create a macro, or use the [**AddConsoleAlias**](addconsolealias.md) function. The following example uses Doskey.exe:

**doskey test=cd \\***a\_very\_long\_path***\\test**

The following call to [**AddConsoleAlias**](addconsolealias.md) creates the same console alias:

``` syntax
AddConsoleAlias( TEXT("test"), 
                 TEXT("cd \\<a_very_long_path>\\test"), 
                 TEXT("cmd.exe"));
```

To add parameters to a console alias macro using Doskey.exe, use the batch parameters $1 through $9. For more information on the special codes that can be used in Doskey macro definitions, see the command-line help for Doskey.exe or [Doskey](http://go.microsoft.com/fwlink/p/?linkid=196265) on TechNet.

All instances of an executable file running in the same console window share any defined console aliases. Multiple instances of the same executable file running in different console windows do not share console aliases. Different executable files running in the same console window do not share console aliases.

To retrieve the target string for a specified source string and executable file, use the [**GetConsoleAlias**](getconsolealias.md) function. To retrieve all aliases for a specified executable file, use the [**GetConsoleAliases**](getconsolealiases.md) function. To retrieve the names of all aliases for which console aliases have been defined, use the [**GetConsoleAliasExes**](getconsolealiasexes.md) function.

 

 




