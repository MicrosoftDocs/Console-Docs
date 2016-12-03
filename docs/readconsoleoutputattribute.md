---
title: ReadConsoleOutputAttribute function
description: Copies a specified number of character attributes from consecutive cells of a console screen buffer, beginning at a specified location.
author: bitcrazed
ms.author: richturn;miniksa


MS-HAID:
- '\_win32\_readconsoleoutputattribute'
- 'base.readconsoleoutputattribute'
- 'consoles.readconsoleoutputattribute'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: c3e35779-a487-47f1-8d07-0d5fae99d54a
keywords: ["ReadConsoleOutputAttribute function Consoles"]
topic_type:
- apiref
api_name:
- ReadConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
---

# ReadConsoleOutputAttribute function


Copies a specified number of character attributes from consecutive cells of a console screen buffer, beginning at a specified location.

Syntax
------

```ManagedCPlusPlus
BOOL WINAPI ReadConsoleOutputAttribute(
  _In_  HANDLE  hConsoleOutput,
  _Out_ LPWORD  lpAttribute,
  _In_  DWORD   nLength,
  _In_  COORD   dwReadCoord,
  _Out_ LPDWORD lpNumberOfAttrsRead
);
```

Parameters
----------

*hConsoleOutput* \[in\]  
A handle to the console screen buffer. The handle must have the **GENERIC\_READ** access right. For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).

*lpAttribute* \[out\]  
A pointer to a buffer that receives the attributes being used by the console screen buffer.

The storage for this buffer is allocated from a shared heap for the process that is 64 KB in size. The maximum size of the buffer will depend on heap usage.

For more information, see [Character Attributes](console-screen-buffers.md#-win32-character-attributes).

*nLength* \[in\]  
The number of screen buffer character cells from which to read. The size of the buffer pointed to by the *lpAttribute* parameter should be `nLength * sizeof(WORD)`.

*dwReadCoord* \[in\]  
The coordinates of the first cell in the console screen buffer from which to read, in characters. The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.

*lpNumberOfAttrsRead* \[out\]  
A pointer to a variable that receives the number of attributes actually read.

Return value
------------

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

Remarks
-------

If the number of attributes to be read from extends beyond the end of the specified screen buffer row, attributes are read from the next row. If the number of attributes to be read from extends beyond the end of the console screen buffer, attributes up to the end of the console screen buffer are read.

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

[**COORD**](coord-str.md)

[Low-Level Console Output Functions](low-level-console-output-functions.md)

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)

[**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md)

[**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)

 

 




