---
title: WriteConsoleInput function
description: Writes data directly to the console input buffer.
MS-HAID:
- '\_win32\_writeconsoleinput'
- 'base.writeconsoleinput'
- 'consoles.writeconsoleinput'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: ad06231f-5063-4aff-b14d-8df5e6e42430
keywords: ["WriteConsoleInput function Consoles"]
topic_type:
- apiref
api_name:
- WriteConsoleInput
- WriteConsoleInputA
- WriteConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
---

# WriteConsoleInput function


Writes data directly to the console input buffer.

Syntax
------

```ManagedCPlusPlus
BOOL WINAPI WriteConsoleInput(
  _In_        HANDLE       hConsoleInput,
  _In_  const INPUT_RECORD *lpBuffer,
  _In_        DWORD        nLength,
  _Out_       LPDWORD      lpNumberOfEventsWritten
);
```

Parameters
----------

*hConsoleInput* \[in\]  
A handle to the console input buffer. The handle must have the **GENERIC\_WRITE** access right. For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).

*lpBuffer* \[in\]  
A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that contain data to be written to the input buffer.

The storage for this buffer is allocated from a shared heap for the process that is 64 KB in size. The maximum size of the buffer will depend on heap usage.

*nLength* \[in\]  
The number of input records to be written.

*lpNumberOfEventsWritten* \[out\]  
A pointer to a variable that receives the number of input records actually written.

Return value
------------

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

Remarks
-------

**WriteConsoleInput** places input records into the input buffer behind any pending events in the buffer. The input buffer grows dynamically, if necessary, to hold as many events as are written.

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
<td><p><strong>WriteConsoleInputW</strong> (Unicode) and <strong>WriteConsoleInputA</strong> (ANSI)</p></td>
</tr>
</tbody>
</table>

## See also


[Console Functions](console-functions.md)

[**INPUT\_RECORD**](input-record-str.md)

[Low-Level Console Input Functions](low-level-console-input-functions.md)

[**MapVirtualKey**](https://msdn.microsoft.com/library/windows/desktop/ms646306)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**VkKeyScan**](https://msdn.microsoft.com/library/windows/desktop/ms646329)

 

 




