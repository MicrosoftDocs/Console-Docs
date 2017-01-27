---
title: SetCurrentConsoleFontEx function
description: Sets extended information about the current console font.
author: miniksa
ms.author: miniksa
ms.HAID:
- 'base.setcurrentconsolefontex'
- 'consoles.setcurrentconsolefontex'
ms.Attr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: fbc31e2a-31df-4e9e-9f61-35a4ff812f8f
keywords: ["SetCurrentConsoleFontEx function Consoles"]
topic_type:
- apiref
api_name:
- SetCurrentConsoleFontEx
api_location:
- Kernel32.dll
api_type:
- DllExport
---

# SetCurrentConsoleFontEx function


Sets extended information about the current console font.

Syntax
------

```C++
BOOL WINAPI SetCurrentConsoleFontEx(
  _In_ HANDLE               hConsoleOutput,
  _In_ BOOL                 bMaximumWindow,
  _In_ PCONSOLE_FONT_INFOEX lpConsoleCurrentFontEx
);
```

Parameters
----------

*hConsoleOutput* \[in\]  
A handle to the console screen buffer. The handle must have the **GENERIC\_WRITE** access right. For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).

*bMaximumWindow* \[in\]  
If this parameter is **TRUE**, font information is set for the maximum window size. If this parameter is **FALSE**, font information is set for the current window size.

*lpConsoleCurrentFontEx* \[in\]  
A pointer to a [**CONSOLE\_FONT\_INFOEX**](console-font-infoex.md) structure that contains the font information.

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
<td><p>Windows Vista [desktop apps only]</p></td>
</tr>
<tr class="even">
<td><p>Minimum supported server</p></td>
<td><p>Windows Server 2008 [desktop apps only]</p></td>
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
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <span id="see_also"></span>See also


[Console Functions](console-functions.md)

[**CONSOLE\_FONT\_INFOEX**](console-font-infoex.md)

 

 




