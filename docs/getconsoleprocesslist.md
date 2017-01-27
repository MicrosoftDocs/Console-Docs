---
title: GetConsoleProcessList function
description: Retrieves a list of the processes attached to the current console.
author: miniksa
ms.author: miniksa
ms.assetid: 3d21103b-662d-4393-ae3f-773cd9e4a930
keywords: ["GetConsoleProcessList function Consoles"]
topic_type:
- apiref
api_name:
- GetConsoleProcessList
api_location:
- Kernel32.dll
api_type:
- DllExport
---

# GetConsoleProcessList function


Retrieves a list of the processes attached to the current console.

Syntax
------

```C++
DWORD WINAPI GetConsoleProcessList(
  _Out_ LPDWORD lpdwProcessList,
  _In_  DWORD   dwProcessCount
);
```

Parameters
----------

*lpdwProcessList* \[out\]  
A pointer to a buffer that receives an array of process identifiers upon success.

The storage for this buffer is allocated from a shared heap for the process that is 64 KB in size. The maximum size of the buffer will depend on heap usage.

*dwProcessCount* \[in\]  
The maximum number of process identifiers that can be stored in the *lpdwProcessList* buffer.

Return value
------------

If the function succeeds, the return value is less than or equal to *dwProcessCount* and represents the number of process identifiers stored in the *lpdwProcessList* buffer.

If the buffer is too small to hold all the valid process identifiers, the return value is the required number of array elements. The function will have stored no identifiers in the buffer. In this situation, use the return value to allocate a buffer that is large enough to store the entire list and call the function again.

If the return value is zero, the function has failed, because every console has at least one process associated with it. To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

Remarks
-------

To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later. For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).

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


[**AttachConsole**](attachconsole.md)

[Console Functions](console-functions.md)

 

 




