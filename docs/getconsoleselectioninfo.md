---
title: GetConsoleSelectionInfo function
description: Retrieves information about the current console selection.
author: bitcrazed
ms.author: richturn
ms.topic: article
ms.prod: console
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- '\_win32\_getconsoleselectioninfo'
- 'base.getconsoleselectioninfo'
- 'consoles.getconsoleselectioninfo'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 912efe9d-75dd-43bd-8dca-08671b5ed79c

topic_type:
- apiref
api_name:
- GetConsoleSelectionInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
---

# GetConsoleSelectionInfo function


Retrieves information about the current console selection.

Syntax
------

```C
BOOL WINAPI GetConsoleSelectionInfo(
  _Out_ PCONSOLE_SELECTION_INFO lpConsoleSelectionInfo
);
```

Parameters
----------

*lpConsoleSelectionInfo* \[out\]  
A pointer to a [**CONSOLE\_SELECTION\_INFO**](console-selection-info-str.md) structure that receives the selection information.

Return value
------------

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

Remarks
-------

To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later. For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).

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
<td><p>Windows XP [desktop apps only]</p></td>
</tr>
<tr class="even">
<td><p>Minimum supported server</p></td>
<td><p>Windows Server 2003 [desktop apps only]</p></td>
</tr>
<tr class="odd">
<td><p>Header</p></td>
<td>ConsoleApi3.h (via Wincon.h, include Windows.h)</td>
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
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <span id="see_also"></span>See also


[Console Functions](console-functions.md)

[Console Selection](console-selection.md)

[**CONSOLE\_SELECTION\_INFO**](console-selection-info-str.md)

 

 




