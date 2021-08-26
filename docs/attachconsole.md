---
title: AttachConsole function
description: See reference information about the AttachConsole function, which attaches the calling process to the console of the specified process.
author: miniksa
ms.author: miniksa
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

Attaches the calling process to the console of the specified process as a client application.

## Syntax

```C
BOOL WINAPI AttachConsole(
  _In_ DWORD dwProcessId
);
```

## Parameters

*dwProcessId* \[in\]  
The identifier of the process whose console is to be used. This parameter can be one of the following values.

| Value | Meaning |
|-|-|
| *pid* | Use the console of the specified process. |
| **ATTACH\_PARENT\_PROCESS** `(DWORD)-1` | Use the console of the parent of the current process. |

## Return value

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## Remarks

A process can be attached to at most one console. If the calling process is already attached to a console, the error code returned is **ERROR\_ACCESS\_DENIED**. If the specified process does not have a console, the error code returned is **ERROR\_INVALID\_HANDLE**. If the specified process does not exist, the error code returned is **ERROR\_INVALID\_PARAMETER**.

A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its console. If other processes share the console, the console is not destroyed, but the process that called **FreeConsole** cannot refer to it. A console is closed when the last process attached to it terminates or calls **FreeConsole**. After a process calls **FreeConsole**, it can call the [**AllocConsole**](allocconsole.md) function to create a new console or **AttachConsole** to attach to another console.

This function is primarily useful to applications that were linked with [**/SUBSYSTEM:WINDOWS**](/cpp/build/reference/subsystem-specify-subsystem), which implies to the operating system that a console is not needed before entering the program's main method. In that instance, the standard handles retrieved with [**GetStdHandle**](getstdhandle.md) will likely be invalid on startup until **AttachConsole** is called. The exception to this is if the application is launched with handle inheritance by its parent process.

To compile an application that uses this function, define **\_WIN32\_WINNT** as `0x0501` or later. For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows XP \[desktop apps only\] |
| Minimum supported server | Windows Server 2003 \[desktop apps only\] |
| Header | ConsoleApi.h (via WinCon.h, include Windows.h) |
| Library | Kernel32.lib |
| DLL | Kernel32.dll |

## See also

[Console Functions](console-functions.md)

[Consoles](consoles.md)

[**AllocConsole**](allocconsole.md)

[**FreeConsole**](freeconsole.md)

[**GetConsoleProcessList**](getconsoleprocesslist.md)
