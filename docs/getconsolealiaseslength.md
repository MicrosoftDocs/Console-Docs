---
title: GetConsoleAliasesLength function
description: Retrieves the required size for the buffer used by the GetConsoleAliases function.
author: miniksa
ms.author: miniksa
ms.HAID:
- 'base.getconsolealiaseslength'
- 'consoles.getconsolealiaseslength'
ms.Attr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 29e49eba-0864-4ed7-af82-1ba639261c40
keywords: ["GetConsoleAliasesLength function Consoles"]
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


Retrieves the required size for the buffer used by the [**GetConsoleAliases**](getconsolealiases.md) function.

Syntax
------

```ManagedCPlusPlus
DWORD WINAPI GetConsoleAliasesLength(
  _In_ LPTSTR lpExeName
);
```

Parameters
----------

*lpExeName* \[in\]  
The name of the executable file whose console aliases are to be retrieved.

Return value
------------

The size of the buffer required to store all console aliases defined for this executable file, in bytes.

Remarks
-------

To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later. For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).

Requirements
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Minimum supported client</p></td>
<td><p>Windows 2000 Professional [desktop apps only]</p></td>
</tr>
<tr class="even">
<td><p>Minimum supported server</p></td>
<td><p>Windows 2000 Server [desktop apps only]</p></td>
</tr>
<tr class="odd">
<td><p>Header</p></td>
<td>Wincon.h (include Windows.h)</td>
</tr>
<tr class="even">
<td><p>Library</p></td>
<td>Kernel32.lib</td>
</tr>
<tr class="odd">
<td><p>DLL</p></td>
<td>Kernel32.dll</td>
</tr>
<tr class="even">
<td><p>Unicode and ANSI names</p></td>
<td><p><strong>GetConsoleAliasesLengthW</strong> (Unicode) and <strong>GetConsoleAliasesLengthA</strong> (ANSI)</p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <span id="see_also"></span>See also


[**AddConsoleAlias**](addconsolealias.md)

[Console Aliases](console-aliases.md)

[Console Functions](console-functions.md)

[**GetConsoleAlias**](getconsolealias.md)

[**GetConsoleAliases**](getconsolealiases.md)

[**GetConsoleAliasExes**](getconsolealiasexes.md)

 

 




