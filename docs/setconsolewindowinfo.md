---
title: SetConsoleWindowInfo function
description: Sets the current size and position of a console screen buffer's window.
author: bitcrazed
ms.author: richturn
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- '\_win32\_setconsolewindowinfo'
- 'base.setconsolewindowinfo'
- 'consoles.setconsolewindowinfo'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: ad16a8fe-ca91-41d6-93b1-8cce6d54b1da

topic_type:
- apiref
api_name:
- SetConsoleWindowInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
---

# SetConsoleWindowInfo function


Sets the current size and position of a console screen buffer's window.

Syntax
------

```C
BOOL WINAPI SetConsoleWindowInfo(
  _In_       HANDLE     hConsoleOutput,
  _In_       BOOL       bAbsolute,
  _In_ const SMALL_RECT *lpConsoleWindow
);
```

Parameters
----------

*hConsoleOutput* \[in\]  
A handle to the console screen buffer. The handle must have the **GENERIC\_READ** access right. For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).

*bAbsolute* \[in\]  
If this parameter is **TRUE**, the coordinates specify the new upper-left and lower-right corners of the window. If it is **FALSE**, the coordinates are relative to the current window-corner coordinates.

*lpConsoleWindow* \[in\]  
A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure that specifies the new upper-left and lower-right corners of the window.

Return value
------------

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

Remarks
-------

The function fails if the specified window rectangle extends beyond the boundaries of the console screen buffer. This means that the **Top** and **Left** members of the *lpConsoleWindow* rectangle (or the calculated top and left coordinates, if *bAbsolute* is FALSE) cannot be less than zero. Similarly, the **Bottom** and **Right** members (or the calculated bottom and right coordinates) cannot be greater than (screen buffer height – 1) and (screen buffer width – 1), respectively. The function also fails if the **Right** member (or calculated right coordinate) is less than or equal to the **Left** member (or calculated left coordinate) or if the **Bottom** member (or calculated bottom coordinate) is less than or equal to the **Top** member (or calculated top coordinate).

For consoles with more than one screen buffer, changing the window location for one screen buffer does not affect the window locations of the other screen buffers.

To determine the current size and position of a screen buffer's window, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function. This function also returns the maximum size of the window, given the current screen buffer size, the current font size, and the screen size. The [**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md) function returns the maximum window size given the current font and screen sizes, but it does not consider the size of the console screen buffer.

**SetConsoleWindowInfo** can be used to scroll the contents of the console screen buffer by shifting the position of the window rectangle without changing its size.

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

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md)

[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md)

[Scrolling the Screen Buffer](scrolling-the-screen-buffer.md)

[**SMALL\_RECT**](small-rect-str.md)

 

 




