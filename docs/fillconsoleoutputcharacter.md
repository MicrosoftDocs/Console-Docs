---
title: FillConsoleOutputCharacter function
description: Writes a character to the console screen buffer a specified number of times, beginning at the specified coordinates.
author: bitcrazed
ms.author: richturn
ms.topic: article
ms.prod: console
keywords: console, character mode applications, command line applications, terminal applications, console api
---

# FillConsoleOutputCharacter function


Writes a character to the console screen buffer a specified number of times, beginning at the specified coordinates.

Syntax
------

```ManagedCPlusPlus
BOOL WINAPI FillConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _In_  TCHAR   cCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfCharsWritten
);
```

Parameters
----------

*hConsoleOutput* \[in\]  
A handle to the console screen buffer. The handle must have the **GENERIC\_WRITE** access right. For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).

*cCharacter* \[in\]  
The character to be written to the console screen buffer.

*nLength* \[in\]  
The number of character cells to which the character should be written.

*dwWriteCoord* \[in\]  
A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell to which the character is to be written.

*lpNumberOfCharsWritten* \[out\]  
A pointer to a variable that receives the number of characters actually written to the console screen buffer.

Return value
------------

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

Remarks
-------

If the number of characters to write to extends beyond the end of the specified row in the console screen buffer, characters are written to the next row. If the number of characters to write to extends beyond the end of the console screen buffer, the characters are written up to the end of the console screen buffer.

The attribute values at the positions written are not changed.

This function uses either Unicode characters or 8-bit characters from the console's current code page. The console's code page defaults initially to the system's OEM code page. To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.

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
<td><p><strong>FillConsoleOutputCharacterW</strong> (Unicode) and <strong>FillConsoleOutputCharacterA</strong> (ANSI)</p></td>
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

[**COORD**](coord-str.md)

[**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md)

[Low-Level Console Output Functions](low-level-console-output-functions.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)

 

 




