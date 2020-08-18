---
title: GetLargestConsoleWindowSize function
description: Retrieves the size of the largest possible console window, based on the current font and the size of the display.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- '\_win32\_getlargestconsolewindowsize'
- 'base.getlargestconsolewindowsize'
- 'consoles.getlargestconsolewindowsize'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 3e5897f3-4987-4a82-ab19-06c0b231ba67

topic_type:
- apiref
api_name:
- GetLargestConsoleWindowSize
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
---

# GetLargestConsoleWindowSize function


Retrieves the size of the largest possible console window, based on the current font and the size of the display.

Syntax
------

```C
COORD WINAPI GetLargestConsoleWindowSize(
  _In_ HANDLE hConsoleOutput
);
```

Parameters
----------

*hConsoleOutput* \[in\]  
A handle to the console screen buffer.

Return value
------------

If the function succeeds, the return value is a [**COORD**](coord-str.md) structure that specifies the number of character cell columns (**X** member) and rows (**Y** member) in the largest possible console window. Otherwise, the members of the structure are zero.

To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

Remarks
-------

The function does not take into consideration the size of the console screen buffer, which means that the window size returned may be larger than the size of the console screen buffer. The [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function can be used to determine the maximum size of the console window, given the current screen buffer size, the current font, and the display size.

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

[**COORD**](coord-str.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**SetConsoleWindowInfo**](setconsolewindowinfo.md)

[Window and Screen Buffer Size](window-and-screen-buffer-size.md)

 

 




