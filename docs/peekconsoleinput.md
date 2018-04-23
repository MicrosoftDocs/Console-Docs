---
title: PeekConsoleInput function
description: Reads data from the specified console input buffer without removing it from the buffer.
author: bitcrazed
ms.author: richturn
ms.topic: article
ms.prod: console
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- '\_win32\_peekconsoleinput'
- 'base.peekconsoleinput'
- 'consoles.peekconsoleinput'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 9982dc20-43bd-4ee3-a68d-157c9134daca

topic_type:
- apiref
api_name:
- PeekConsoleInput
- PeekConsoleInputA
- PeekConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
---

# PeekConsoleInput function


Reads data from the specified console input buffer without removing it from the buffer.

Syntax
------

```ManagedCPlusPlus
BOOL WINAPI PeekConsoleInput(
  _In_  HANDLE        hConsoleInput,
  _Out_ PINPUT_RECORD lpBuffer,
  _In_  DWORD         nLength,
  _Out_ LPDWORD       lpNumberOfEventsRead
);
```

Parameters
----------

*hConsoleInput* \[in\]  
A handle to the console input buffer. The handle must have the **GENERIC\_READ** access right. For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).

*lpBuffer* \[out\]  
A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that receives the input buffer data.

*nLength* \[in\]  
The size of the array pointed to by the *lpBuffer* parameter, in array elements.

*lpNumberOfEventsRead* \[out\]  
A pointer to a variable that receives the number of input records read.

Return value
------------

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

Remarks
-------

If the number of records requested exceeds the number of records available in the buffer, the number available is read. If no data is available, the function returns immediately.

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
<td><p><strong>PeekConsoleInputW</strong> (Unicode) and <strong>PeekConsoleInputA</strong> (ANSI)</p></td>
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

[**ReadConsoleInput**](readconsoleinput.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**WriteConsoleInput**](writeconsoleinput.md)

[**INPUT\_RECORD**](input-record-str.md)

 

 




