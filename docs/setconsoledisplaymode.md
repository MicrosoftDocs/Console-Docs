---
title: SetConsoleDisplayMode function
description: See reference information about the SetConsoleDisplayMode function, which sets the display mode of the specified console screen buffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi3/SetConsoleDisplayMode
- wincon/SetConsoleDisplayMode
- SetConsoleDisplayMode
MS-HAID:
- 'base.setconsoledisplaymode'
- 'consoles.setconsoledisplaymode'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 27437a85-f784-41fc-8279-9fe089b0a744

topic_type:
- apiref
api_name:
- SetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
---

# SetConsoleDisplayMode function

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Sets the display mode of the specified console screen buffer.

Syntax
------

```C
BOOL WINAPI SetConsoleDisplayMode(
  _In_      HANDLE hConsoleOutput,
  _In_      DWORD  dwFlags,
  _Out_opt_ PCOORD lpNewScreenBufferDimensions
);
```

Parameters
----------

*hConsoleOutput* \[in\]  
A handle to the console screen buffer.

*dwFlags* \[in\]  
The display mode of the console. This parameter can be one or more of the following values.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Value</th>
<th>Meaning</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="CONSOLE_FULLSCREEN_MODE"></span><span id="console_fullscreen_mode"></span>
<strong>CONSOLE_FULLSCREEN_MODE</strong>
1</td>
<td><p>Text is displayed in full-screen mode.</p></td>
</tr>
<tr class="even">
<td><span id="CONSOLE_WINDOWED_MODE"></span><span id="console_windowed_mode"></span>
<strong>CONSOLE_WINDOWED_MODE</strong>
2</td>
<td><p>Text is displayed in a console window.</p></td>
</tr>
</tbody>
</table>

 

*lpNewScreenBufferDimensions* \[out, optional\]  
A pointer to a [**COORD**](coord-str.md) structure that receives the new dimensions of the screen buffer, in characters.

Return value
------------

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

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
<td><p>Windows XP [desktop apps only]</p></td>
</tr>
<tr class="even">
<td><p>Minimum supported server</p></td>
<td><p>Windows Server 2003 [desktop apps only]</p></td>
</tr>
<tr class="odd">
<td><p>Header</p></td>
<td>ConsoleApi3.h (via Wincon.h, include Windows.h)</td>
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

[Console Modes](console-modes.md)

[**GetConsoleDisplayMode**](getconsoledisplaymode.md)
