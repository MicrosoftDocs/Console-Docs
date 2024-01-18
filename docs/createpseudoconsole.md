---
title: CreatePseudoConsole function
description: See reference information about the CreatePseudoConsole function, which allocates a new pseudoconsole for the calling process.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api, conpty, pseudoconsole
topic_type:
- apiref
api_name:
- CreatePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
---

# CreatePseudoConsole function


Creates a new pseudoconsole object for the calling process.

Syntax
------

```C
HRESULT WINAPI CreatePseudoConsole(
    _In_ COORD size,
    _In_ HANDLE hInput,
    _In_ HANDLE hOutput,
    _In_ DWORD dwFlags,
    _Out_ HPCON* phPC
);
```

Parameters
----------

*size* \[in\]  
The dimensions of the window/buffer in count of characters that will be used on initial creation of the pseudoconsole. This can be adjusted later with [ResizePseudoConsole](resizepseudoconsole.md).

*hInput* \[in\]  
An open handle to a stream of data that represents user input to the device. This is currently restricted to [synchronous](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) I/O.

*hOutput* \[in\]  
An open handle to a stream of data that represents application output from the device. This is currently restricted to [synchronous](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) I/O.

*dwFlags* \[in\]  
The value can be one of the following:
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
<td><strong>0</strong></td>
<td><p>Perform a standard pseudoconsole creation.</p></td>
</tr>
<tr class="even">
<td><span id="PSEUDOCONSOLE_INHERIT_CURSOR"></span><span id="pseudoconsole_inherit_cursor"></span>
<strong>PSEUDOCONSOLE_INHERIT_CURSOR</strong>
(DWORD)1</td>
<td><p>The created pseudoconsole session will attempt to inherit the cursor position of the parent console.</p></td>
</tr>
</tbody>
</table>

*phPC* \[out\]  
Pointer to a location that will receive a handle to the new pseudoconsole device.

Return value
------------

Type: **HRESULT**

If this method succeeds, it returns **S_OK**. Otherwise, it returns an **HRESULT** error code.

Remarks
-------

This function is primarily used by applications attempting to be a terminal window for a command-line user interface (CUI) application. The callers become responsible for presentation of the information on the output stream and for collecting user input and serializing it into the input stream.

The input and output streams encoded as UTF-8 contain plain text interleaved with [Virtual Terminal Sequences](console-virtual-terminal-sequences.md). 

On the output stream, the [virtual terminal sequences](console-virtual-terminal-sequences.md) can be decoded by the calling application to layout and present the plain text in a display window. 

On the input stream, plain text represents standard keyboard keys input by a user. More complicated operations are represented by encoding control keys and mouse movements as [virtual terminal sequences](console-virtual-terminal-sequences.md) embedded in this stream.

The handle created by this function must be closed with [ClosePseudoConsole](closepseudoconsole.md) when operations are complete.

If using `PSEUDOCONSOLE_INHERIT_CURSOR`, the calling application should be prepared to respond to the request for the cursor state in an asynchronous fashion on a background thread by forwarding or interpreting the request for cursor information that will be received on `hOutput` and replying on `hInput`. Failure to do so may cause the calling application to hang while making another request of the pseudoconsole system.

Examples
--------

For a full walkthrough on using this function to establish a psuedoconsole session, please see [Creating a Pseudoconsole Session](creating-a-pseudoconsole-session.md).

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
<td><p>Windows 10 1809 [desktop apps only]</p></td>
</tr>
<tr class="even">
<td><p>Minimum supported server</p></td>
<td><p>Windows Server 2019 [desktop apps only]</p></td>
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


[Pseudoconsoles](pseudoconsoles.md)

[Creating a Pseudoconsole Session](creating-a-pseudoconsole-session.md)

[**ResizePseudoConsole**](resizepseudoconsole.md)

[**ClosePseudoConsole**](closepseudoconsole.md)
