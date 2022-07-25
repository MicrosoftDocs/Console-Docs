---
title: ReadConsoleInputEx function
description: Reads data from a console input buffer with a specified set of flags and removes it from the buffer.
author: DHowett
ms.author: DHowett
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi/ReadConsoleInputEx
- wincon/ReadConsoleInputEx
- ReadConsoleInputEx
- consoleapi/ReadConsoleInputExA
- wincon/ReadConsoleInputExA
- ReadConsoleInputExA
- consoleapi/ReadConsoleInputExW
- wincon/ReadConsoleInputExW
- ReadConsoleInputExW
MS-HAID:
- '\_win32\_readconsoleinputex'
- 'base.readconsoleinputex'
- 'consoles.readconsoleinputex'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 5a9f7b18-cdea-4041-a377-5532d30e0105

topic_type:
- apiref
api_name:
- ReadConsoleInputEx
- ReadConsoleInputExA
- ReadConsoleInputExW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
---

# ReadConsoleInputEx function

Reads data from a console input buffer and removes it from the buffer, with configurable behavior.

<div class="alert"><b>Note</b> This function has no associated import library. This function is available as the resources named <b>ReadConsoleInputExA</b> and <b>ReadConsoleInputExW</b> in Kernel32.dll. You must use the <a href="/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibrarya">LoadLibrary</a> and <a href="/windows/desktop/api/libloaderapi/nf-libloaderapi-getprocaddress">GetProcAddress</a> functions to dynamically link to Kernel32.dll.</div><div> </div>

## Syntax

```C
BOOL WINAPI ReadConsoleInputEx(
  _In_  HANDLE        hConsoleInput,
  _Out_ PINPUT_RECORD lpBuffer,
  _In_  DWORD         nLength,
  _Out_ LPDWORD       lpNumberOfEventsRead,
  _In_  USHORT        wFlags
);
```

## Parameters

*hConsoleInput* \[in\]  
A handle to the console input buffer. The handle must have the **GENERIC\_READ** access right. For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).

*lpBuffer* \[out\]  
A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that receives the input buffer data.

*nLength* \[in\]  
The size of the array pointed to by the *lpBuffer* parameter, in array elements.

*lpNumberOfEventsRead* \[out\]  
A pointer to a variable that receives the number of input records read.

*wFlags* \[in\]

A set of flags (ORed together) that specify the console's reading behavior.

| Value | Meaning |
|-|-|
| **CONSOLE_READ_NOREMOVE** `0x0001` | Leave the events in the input buffer (as in [`PeekConsoleInput`](peekconsoleinput.md)) |
| **CONSOLE_READ_NOWAIT** `0x0002` | Return immediately, even if there are no events in the input buffer.

## Return value

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## Remarks

This function is a configurable version of `ReadConsoleInput`. See the [remarks for `ReadConsoleInput`](readconsoleinput.md) for additional operational details.

Calling `ReadConsoleInputEx` with the flags `CONSOLE_READ_NOMOVE | CONSOLE_READ_NOWAIT` is equivalent to calling [`PeekConsoleInput`](peekconsoleinput.md).

This function does not exist in the Windows Console headers. To gain access to it from a C or C++ application, include the following declarations and dynamically link kernel32.dll as noted above.

```c
#define CONSOLE_READ_NOREMOVE   0x0001
#define CONSOLE_READ_NOWAIT     0x0002

BOOL
WINAPI
ReadConsoleInputExA(
    _In_ HANDLE hConsoleInput,
    _Out_writes_(nLength) PINPUT_RECORD lpBuffer,
    _In_ DWORD nLength,
    _Out_ LPDWORD lpNumberOfEventsRead,
    _In_ USHORT wFlags);

BOOL
WINAPI
ReadConsoleInputExW(
    _In_ HANDLE hConsoleInput,
    _Out_writes_(nLength) PINPUT_RECORD lpBuffer,
    _In_ DWORD nLength,
    _Out_ LPDWORD lpNumberOfEventsRead,
    _In_ USHORT wFlags);
```

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows 7 \[desktop apps only\] |
| Minimum supported server | Windows Server 2003 \[desktop apps only\] |
| Header | none, see remarks |
| Library | none, see remarks |
| DLL | Kernel32.dll |
| Unicode and ANSI names | **ReadConsoleInputExW** (Unicode) and **ReadConsoleInputExA** (ANSI) |

## See also

[Console Functions](console-functions.md)

[**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md)

[**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md)

[**INPUT\_RECORD**](input-record-str.md)

[Low-Level Console Input Functions](low-level-console-input-functions.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsole**](readconsole.md)

[**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**WriteConsoleInput**](writeconsoleinput.md)
