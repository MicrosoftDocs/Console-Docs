---
title: GetConsoleWindow function
description: Retrieves the window handle used by the console associated with the calling process.
author: bitcrazed
ms.author: richturn;miniksa


MS-HAID:
- '\_win32\_getconsolewindow'
- 'base.getconsolewindow'
- 'consoles.getconsolewindow'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: a5ab0b37-45ac-4413-b6ff-73876556ad38
keywords: ["GetConsoleWindow function Consoles"]
topic_type:
- apiref
api_name:
- GetConsoleWindow
api_location:
- Kernel32.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-0.dll
- kernel32legacy.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-1.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-2.dll
- API-MS-Win-DownLevel-Kernel32-l2-1-0.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-3.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-4.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-5.dll
api_type:
- DllExport
---

# GetConsoleWindow function


Retrieves the window handle used by the console associated with the calling process.

Syntax
------

```ManagedCPlusPlus
HWND WINAPI GetConsoleWindow(void);
```

Parameters
----------

This function has no parameters.

Return value
------------

The return value is a handle to the window used by the console associated with the calling process or **NULL** if there is no such associated console.

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
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <span id="see_also"></span>See also


[Console Functions](console-functions.md)

 

 




