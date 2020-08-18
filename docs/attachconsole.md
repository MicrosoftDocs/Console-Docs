---
title: AttachConsole function
description: See reference information about the AttachConsole function, which attaches the calling process to the console of the specified process.
author: bitcrazed
ms.author: richturn
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords: 
- consoleapi/AttachConsole
- wincon/AttachConsole
- AttachConsole
MS-HAID:
- '\_win32\_attachconsole'
- 'base.attachconsole'
- 'consoles.attachconsole'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: c00691c3-5878-4a06-9bf3-6073326f36c4
topic_type:
- apiref
api_name:
- AttachConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
---

# AttachConsole function


Attaches the calling process to the console of the specified process.

Syntax
------

```C
BOOL WINAPI AttachConsole(
  _In_ DWORD dwProcessId
);
```

Parameters
----------

*dwProcessId* \[in\]  
The identifier of the process whose console is to be used. This parameter can be one of the following values.

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
<td><em>pid</em></td>
<td><p>Use the console of the specified process.</p></td>
</tr>
<tr class="even">
<td><span id="ATTACH_PARENT_PROCESS"></span><span id="attach_parent_process"></span>
<strong>ATTACH_PARENT_PROCESS</strong>
(DWORD)-1</td>
<td><p>Use the console of the parent of the current process.</p></td>
</tr>
</tbody>
</table>

 

Return value
------------

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

Remarks
-------

A process can be attached to at most one console. If the calling process is already attached to a console, the error code returned is **ERROR\_ACCESS\_DENIED** (5). If the specified process does not have a console, the error code returned is **ERROR\_INVALID\_HANDLE** (6). If the specified process does not exist, the error code returned is **ERROR\_INVALID\_PARAMETER** (87).

A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its console. If other processes share the console, the console is not destroyed, but the process that called **FreeConsole** cannot refer to it. A console is closed when the last process attached to it terminates or calls **FreeConsole**. After a process calls **FreeConsole**, it can call the [**AllocConsole**](allocconsole.md) function to create a new console or **AttachConsole** to attach to another console.

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
<td>ConsoleApi.h (via Wincon.h, include Windows.h)</td>
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

[Consoles](consoles.md)

[**AllocConsole**](allocconsole.md)

[**FreeConsole**](freeconsole.md)

[**GetConsoleProcessList**](getconsoleprocesslist.md)

 

 




