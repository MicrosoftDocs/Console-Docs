---
title: GetConsoleAlias function
description: Retrieves the text for the specified console alias and executable.
author: miniksa
ms.author: miniksa
ms.HAID:
- 'base.getconsolealias'
- 'consoles.getconsolealias'
ms.Attr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: e8514f24-8121-4fad-94bb-c9eedf7a700d
keywords: ["GetConsoleAlias function Consoles"]
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


Retrieves the text for the specified console alias and executable.

Syntax
------

```C++
DWORD WINAPI GetConsoleAlias(
  _In_  LPTSTR lpSource,
  _Out_ LPTSTR lpTargetBuffer,
  _In_  DWORD  TargetBufferLength,
  _In_  LPTSTR lpExeName
);
```

Parameters
----------

*lpSource* \[in\]  
The console alias whose text is to be retrieved.

*lpTargetBuffer* \[out\]  
A pointer to a buffer that receives the text associated with the console alias.

*TargetBufferLength* \[in\]  
The size of the buffer pointed to by *lpTargetBuffer*, in bytes.

*lpExeName* \[in\]  
The name of the executable file.

Return value
------------

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

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
<td><p><strong>GetConsoleAliasW</strong> (Unicode) and <strong>GetConsoleAliasA</strong> (ANSI)</p></td>
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


[Console Aliases](console-aliases.md)

[Console Functions](console-functions.md)

[**AddConsoleAlias**](addconsolealias.md)

[**GetConsoleAliases**](getconsolealiases.md)

[**GetConsoleAliasExes**](getconsolealiasexes.md)

 

 




