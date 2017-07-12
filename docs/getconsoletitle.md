---
title: GetConsoleTitle function
description: Retrieves the title and size of the title for the current console window.
author: bitcrazed
ms.author: richturn
ms.topic: article
ms.prod: console
keywords: console, character mode applications, command line applications, terminal applications, console api
---

# GetConsoleTitle function


Retrieves the title for the current console window.

Syntax
------

```ManagedCPlusPlus
DWORD WINAPI GetConsoleTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

Parameters
----------

*lpConsoleTitle* \[out\]  
A pointer to a buffer that receives a null-terminated string containing the title. If the buffer is too small to store the title, the function stores as many characters of the title as will fit in the buffer, ending with a null terminator.

The storage for this buffer is allocated from a shared heap for the process that is 64 KB in size. The maximum size of the buffer will depend on heap usage.

*nSize* \[in\]  
The size of the buffer pointed to by the *lpConsoleTitle* parameter, in characters.

Return value
------------

If the function succeeds, the return value is the length of the console window's title, in characters.

If the function fails, the return value is zero and [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) returns the error code.

Remarks
-------

To set the title for a console window, use the [**SetConsoleTitle**](setconsoletitle.md) function. To retrieve the original title string, use the [**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md) function.

This function uses either Unicode characters or 8-bit characters from the console's current code page. The console's code page defaults initially to the system's OEM code page. To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.

Examples
--------

For an example, see [**SetConsoleTitle**](setconsoletitle.md).

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
<td><p><strong>GetConsoleTitleW</strong> (Unicode) and <strong>GetConsoleTitleA</strong> (ANSI)</p></td>
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

[**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**SetConsoleTitle**](setconsoletitle.md)

 

 




