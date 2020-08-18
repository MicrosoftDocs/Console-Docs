---
title: GetConsoleScreenBufferInfo function
description: See reference information about the GetConsoleScreenBufferInfo function, which retrieves information about the specified console screen buffer.
author: bitcrazed
ms.author: richturn
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- wincon/GetConsoleScreenBufferInfo
- GetConsoleScreenBufferInfo
ms.assetid: eafe819e-a99a-4ce1-8898-8860444a31af

topic_type:
- apiref
api_name:
- GetConsoleScreenBufferInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
---

# GetConsoleScreenBufferInfo function


Retrieves information about the specified console screen buffer.

Syntax
------

```C
BOOL WINAPI GetConsoleScreenBufferInfo(
  _In_  HANDLE                      hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFO lpConsoleScreenBufferInfo
);
```

Parameters
----------

*hConsoleOutput* \[in\]  
A handle to the console screen buffer. The handle must have the **GENERIC\_READ** access right. For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).

*lpConsoleScreenBufferInfo* \[out\]  
A pointer to a [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure that receives the console screen buffer information.

Return value
------------

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

Remarks
-------

The rectangle returned in the **srWindow** member of the [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure can be modified and then passed to the [**SetConsoleWindowInfo**](setconsolewindowinfo.md) function to scroll the console screen buffer in the window, to change the size of the window, or both.

All coordinates returned in the [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure are in character-cell coordinates, where the origin (0, 0) is at the upper-left corner of the console screen buffer.

Examples
--------

For an example, see [Scrolling a Screen Buffer's Window](scrolling-a-screen-buffer-s-window.md).

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
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <span id="see_also"></span>See also


[Console Functions](console-functions.md)

[**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md)

[**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md)

[**SetConsoleCursorPosition**](setconsolecursorposition.md)

[**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md)

[**SetConsoleWindowInfo**](setconsolewindowinfo.md)

[Window and Screen Buffer Size](window-and-screen-buffer-size.md)

 

 




