---
title: GetConsoleAliases function
description: Retrieves all of the defined console aliases for the specified executable.
author: bitcrazed
ms.author: richturn
ms.topic: article
ms.prod: console
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- 'base.getconsolealiases'
- 'consoles.getconsolealiases'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 92eefa4e-ffde-4886-afde-5aecf450b425

topic_type:
- apiref
api_name:
- GetConsoleAliases
- GetConsoleAliasesA
- GetConsoleAliasesW
api_location:
- Kernel32.dll
api_type:
- DllExport
---

# GetConsoleAliases function


Retrieves all defined console aliases for the specified executable.

Syntax
------

```ManagedCPlusPlus
DWORD WINAPI GetConsoleAliases(
  _Out_ LPTSTR lpAliasBuffer,
  _In_  DWORD  AliasBufferLength,
  _In_  LPTSTR lpExeName
);
```

Parameters
----------

*lpAliasBuffer* \[out\]  
A pointer to a buffer that receives the aliases.

The format of the data is as follows: *Source1*=*Target1*\\0*Source2*=*Target2*\\0... *SourceN*=*TargetN*\\0, where *N* is the number of console aliases defined.

*AliasBufferLength* \[in\]  
The size of the buffer pointed to by *lpAliasBuffer*, in bytes.

*lpExeName* \[in\]  
The executable file whose aliases are to be retrieved.

Return value
------------

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

Remarks
-------

To determine the required size for the *lpExeName* buffer, use the [**GetConsoleAliasesLength**](getconsolealiaseslength.md) function.

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
<td><p><strong>GetConsoleAliasesW</strong> (Unicode) and <strong>GetConsoleAliasesA</strong> (ANSI)</p></td>
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

[**GetConsoleAliasesLength**](getconsolealiaseslength.md)

[**GetConsoleAliasExes**](getconsolealiasexes.md)

 

 




