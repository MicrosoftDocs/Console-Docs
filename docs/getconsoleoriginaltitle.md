---
title: GetConsoleOriginalTitle function
description: Retrieves the original title for the current console window.
MS-HAID:
- 'base.getconsoleoriginaltitle'
- 'consoles.getconsoleoriginaltitle'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: e3dd02f4-4899-4df0-a960-3b2625c15fee
keywords: ["GetConsoleOriginalTitle function Consoles"]
topic_type:
- apiref
api_name:
- GetConsoleOriginalTitle
- GetConsoleOriginalTitleA
- GetConsoleOriginalTitleW
api_location:
- Kernel32.dll
api_type:
- DllExport
---

# GetConsoleOriginalTitle function


Retrieves the original title for the current console window.

Syntax
------

```ManagedCPlusPlus
DWORD WINAPI GetConsoleOriginalTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

Parameters
----------

*lpConsoleTitle* \[out\]  
A pointer to a buffer that receives a null-terminated string containing the original title.

The storage for this buffer is allocated from a shared heap for the process that is 64 KB in size. The maximum size of the buffer will depend on heap usage.

*nSize* \[in\]  
The size of the *lpConsoleTitle* buffer, in characters.

Return value
------------

If the function succeeds, the return value is the length of the string copied to the buffer, in characters.

If the buffer is not large enough to store the title, the return value is zero and [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) returns **ERROR\_SUCCESS**.

If the function fails, the return value is zero and [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) returns the error code.

Remarks
-------

To set the title for a console window, use the [**SetConsoleTitle**](setconsoletitle.md) function. To retrieve the current title string, use the [**GetConsoleTitle**](getconsoletitle.md) function.

To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0600 or later. For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).

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
<td><p>Unicode and ANSI names</p></td>
<td><p><strong>GetConsoleOriginalTitleW</strong> (Unicode) and <strong>GetConsoleOriginalTitleA</strong> (ANSI)</p></td>
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


[Console Functions](console-functions.md)

[**GetConsoleTitle**](getconsoletitle.md)

[**SetConsoleTitle**](setconsoletitle.md)

 

 




