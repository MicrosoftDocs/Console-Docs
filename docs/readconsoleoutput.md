---
title: ReadConsoleOutput function
description: Reads character and color attribute data from a rectangular block of character cells in a console screen buffer and writes data in the destination buffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi2/ReadConsoleOutput
- wincon/ReadConsoleOutput
- ReadConsoleOutput
- consoleapi2/ReadConsoleOutputA
- wincon/ReadConsoleOutputA
- ReadConsoleOutputA
- consoleapi2/ReadConsoleOutputW
- wincon/ReadConsoleOutputW
- ReadConsoleOutputW
MS-HAID:
- '\_win32\_readconsoleoutput'
- 'base.readconsoleoutput'
- 'consoles.readconsoleoutput'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: d1391684-6a8f-4b5e-9706-11970a957710

topic_type:
- apiref
api_name:
- ReadConsoleOutput
- ReadConsoleOutputA
- ReadConsoleOutputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
---

# ReadConsoleOutput function

[!INCLUDE [not-recommended-banner](.\includes\not-recommended-banner.md)]

Reads character and color attribute data from a rectangular block of character cells in a console screen buffer, and the function writes the data to a rectangular block at a specified location in the destination buffer.

Syntax
------

```C
BOOL WINAPI ReadConsoleOutput(
  _In_    HANDLE      hConsoleOutput,
  _Out_   PCHAR_INFO  lpBuffer,
  _In_    COORD       dwBufferSize,
  _In_    COORD       dwBufferCoord,
  _Inout_ PSMALL_RECT lpReadRegion
);
```

Parameters
----------

*hConsoleOutput* \[in\]  
A handle to the console screen buffer. The handle must have the **GENERIC\_READ** access right. For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).

*lpBuffer* \[out\]  
A pointer to a destination buffer that receives the data read from the console screen buffer. This pointer is treated as the origin of a two-dimensional array of [**CHAR\_INFO**](char-info-str.md) structures whose size is specified by the *dwBufferSize* parameter.

*dwBufferSize* \[in\]  
The size of the *lpBuffer* parameter, in character cells. The **X** member of the [**COORD**](coord-str.md) structure is the number of columns; the **Y** member is the number of rows.

*dwBufferCoord* \[in\]  
The coordinates of the upper-left cell in the *lpBuffer* parameter that receives the data read from the console screen buffer. The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.

*lpReadRegion* \[in, out\]  
A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure. On input, the structure members specify the upper-left and lower-right coordinates of the console screen buffer rectangle from which the function is to read. On output, the structure members specify the actual rectangle that was used.

Return value
------------

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

Remarks
-------

**ReadConsoleOutput** treats the console screen buffer and the destination buffer as two-dimensional arrays (columns and rows of character cells). The rectangle pointed to by the *lpReadRegion* parameter specifies the size and location of the block to be read from the console screen buffer. A destination rectangle of the same size is located with its upper-left cell at the coordinates of the *dwBufferCoord* parameter in the *lpBuffer* array. Data read from the cells in the console screen buffer source rectangle is copied to the corresponding cells in the destination buffer. If the corresponding cell is outside the boundaries of the destination buffer rectangle (whose dimensions are specified by the *dwBufferSize* parameter), the data is not copied.

Cells in the destination buffer corresponding to coordinates that are not within the boundaries of the console screen buffer are left unchanged. In other words, these are the cells for which no screen buffer data is available to be read.

Before **ReadConsoleOutput** returns, it sets the members of the structure pointed to by the *lpReadRegion* parameter to the actual screen buffer rectangle whose cells were copied into the destination buffer. This rectangle reflects the cells in the source rectangle for which there existed a corresponding cell in the destination buffer, because **ReadConsoleOutput** clips the dimensions of the source rectangle to fit the boundaries of the console screen buffer.

If the rectangle specified by *lpReadRegion* lies completely outside the boundaries of the console screen buffer, or if the corresponding rectangle is positioned completely outside the boundaries of the destination buffer, no data is copied. In this case, the function returns with the members of the structure pointed to by the *lpReadRegion* parameter set such that the **Right** member is less than the **Left**, or the **Bottom** member is less than the **Top**. To determine the size of the console screen buffer, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.

The **ReadConsoleOutput** function has no effect on the console screen buffer's cursor position. The contents of the console screen buffer are not changed by the function.

This function uses either Unicode characters or 8-bit characters from the console's current code page. The console's code page defaults initially to the system's OEM code page. To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.

Examples
--------

For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).

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
<td>ConsoleApi2.h (via Wincon.h, include Windows.h)</td>
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
<td><p><strong>ReadConsoleOutputW</strong> (Unicode) and <strong>ReadConsoleOutputA</strong> (ANSI)</p></td>
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

[Low-Level Console Output Functions](low-level-console-output-functions.md)

[**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md)

[**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**SMALL\_RECT**](small-rect-str.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)

[**CHAR\_INFO**](char-info-str.md)

[**COORD**](coord-str.md)

 

 




