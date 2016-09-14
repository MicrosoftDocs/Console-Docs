---
title: SetConsoleCursorInfo function
description: Sets the size and visibility of the cursor for the specified console screen buffer.
MS-HAID:
- '\_win32\_setconsolecursorinfo'
- 'base.setconsolecursorinfo'
- 'consoles.setconsolecursorinfo'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: c98cbffb-18de-41e8-bba7-5fb46a0c5d25
keywords: ["SetConsoleCursorInfo function Consoles"]
topic_type:
- apiref
api_name:
- SetConsoleCursorInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
---

# SetConsoleCursorInfo function


Sets the size and visibility of the cursor for the specified console screen buffer.

Syntax
------

```ManagedCPlusPlus
BOOL WINAPI SetConsoleCursorInfo(
  _In_       HANDLE              hConsoleOutput,
  _In_ const CONSOLE_CURSOR_INFO *lpConsoleCursorInfo
);
```

Parameters
----------

*hConsoleOutput* \[in\]  
A handle to the console screen buffer. The handle must have the **GENERIC\_READ** access right. For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).

*lpConsoleCursorInfo* \[in\]  
A pointer to a [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure that provides the new specifications for the console screen buffer's cursor.

Return value
------------

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

Remarks
-------

When a screen buffer's cursor is visible, its appearance can vary, ranging from completely filling a character cell to showing up as a horizontal line at the bottom of the cell. The **dwSize** member of the [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure specifies the percentage of a character cell that is filled by the cursor. If this member is less than 1 or greater than 100, **SetConsoleCursorInfo** fails.

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
</tbody>
</table>

## See also


[Console Functions](console-functions.md)

[Console Screen Buffers](console-screen-buffers.md)

[**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md)

[**GetConsoleCursorInfo**](getconsolecursorinfo.md)

[**SetConsoleCursorPosition**](setconsolecursorposition.md)

 

 




