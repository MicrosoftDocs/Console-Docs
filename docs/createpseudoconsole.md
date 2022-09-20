---
title: CreatePseudoConsole function
description: See reference information about the CreatePseudoConsole function, which allocates a new pseudoconsole for the calling process.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: windows
keywords: console, character mode applications, command line applications, terminal applications, console api, conpty, pseudoconsole
f1_keywords:
- consoleapi/CreatePseudoConsole
- CreatePseudoConsole
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

## Syntax

```C
HRESULT WINAPI CreatePseudoConsole(
    _In_ COORD size,
    _In_ HANDLE hInput,
    _In_ HANDLE hOutput,
    _In_ DWORD dwFlags,
    _Out_ HPCON* phPC
);
```

## Parameters

*size* \[in\]  
The dimensions of the window/buffer in count of characters that will be used on initial creation of the pseudoconsole. This can be adjusted later with [ResizePseudoConsole](resizepseudoconsole.md).

*hInput* \[in\]  
An open handle to a stream of data that represents user input to the device. This is currently restricted to [synchronous](/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) I/O.

*hOutput* \[in\]  
An open handle to a stream of data that represents application output from the device. This is currently restricted to [synchronous](/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) I/O.

*dwFlags* \[in\]  
The value can be one of the following:

| Value | Meaning |
|-|-|
| **0** | Perform a standard pseudoconsole creation. |
| **PSEUDOCONSOLE_INHERIT_CURSOR** (DWORD)1 | The created pseudoconsole session will attempt to inherit the cursor position of the parent console. |

*phPC* \[out\]  
Pointer to a location that will receive a handle to the new pseudoconsole device.

## Return value

Type: **HRESULT**

If this method succeeds, it returns **S_OK**. Otherwise, it returns an **HRESULT** error code.

## Remarks

This function is primarily used by applications attempting to be a terminal window for a command-line user interface (CUI) application. The callers become responsible for presentation of the information on the output stream and for collecting user input and serializing it into the input stream.

The input and output streams encoded as UTF-8 contain plain text interleaved with [Virtual Terminal Sequences](console-virtual-terminal-sequences.md).

On the output stream, the [virtual terminal sequences](console-virtual-terminal-sequences.md) can be decoded by the calling application to layout and present the plain text in a display window.

On the input stream, plain text represents standard keyboard keys input by a user. More complicated operations are represented by encoding control keys and mouse movements as [virtual terminal sequences](console-virtual-terminal-sequences.md) embedded in this stream.

The handle created by this function must be closed with [ClosePseudoConsole](closepseudoconsole.md) when operations are complete.

If using `PSEUDOCONSOLE_INHERIT_CURSOR`, the calling application should be prepared to respond to the request for the cursor state in an asynchronous fashion on a background thread by forwarding or interpreting the request for cursor information that will be received on `hOutput` and replying on `hInput`. Failure to do so may cause the calling application to hang while making another request of the pseudoconsole system.

## Examples

For a full walkthrough on using this function to establish a pseudoconsole session, please see [Creating a Pseudoconsole Session](creating-a-pseudoconsole-session.md).

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows 10 October 2018 Update (version 1809) \[desktop apps only\] |
| Minimum supported server | Windows Server 2019 \[desktop apps only\] |
| Header | ConsoleApi.h (via WinCon.h, include Windows.h) |
| Library | Kernel32.lib |
| DLL | Kernel32.dll |

## See also

[Pseudoconsoles](pseudoconsoles.md)

[Creating a Pseudoconsole Session](creating-a-pseudoconsole-session.md)

[**ResizePseudoConsole**](resizepseudoconsole.md)

[**ClosePseudoConsole**](closepseudoconsole.md)