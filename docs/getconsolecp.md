---
title: GetConsoleCP function
description: Retrieves the input code page used by the console associated with the calling process.
author: bitcrazed
ms.author: richturn;miniksa


MS-HAID:
- '\_win32\_getconsolecp'
- 'base.getconsolecp'
- 'consoles.getconsolecp'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 9e0af6d9-0f5c-45b3-a686-22449d26de47
keywords: ["GetConsoleCP function Consoles"]
topic_type:
- apiref
api_name:
- GetConsoleCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
---

# GetConsoleCP function


Retrieves the input code page used by the console associated with the calling process. A console uses its input code page to translate keyboard input into the corresponding character value.

Syntax
------

```ManagedCPlusPlus
UINT WINAPI GetConsoleCP(void);
```

Parameters
----------

This function has no parameters.

Return value
------------

The return value is a code that identifies the code page. For a list of identifiers, see [Code Page Identifiers](https://msdn.microsoft.com/library/windows/desktop/dd317756).

Remarks
-------

A code page maps 256 character codes to individual characters. Different code pages include different special characters, typically customized for a language or a group of languages. To retrieve more information about a code page, including it's name, see the [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) function.

To set a console's input code page, use the [**SetConsoleCP**](setconsolecp.md) function. To set and query a console's output code page, use the [**SetConsoleOutputCP**](setconsoleoutputcp.md) and [**GetConsoleOutputCP**](getconsoleoutputcp.md) functions.

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


[Console Code Pages](console-code-pages.md)

[Console Functions](console-functions.md)

[**GetConsoleOutputCP**](getconsoleoutputcp.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

 

 




