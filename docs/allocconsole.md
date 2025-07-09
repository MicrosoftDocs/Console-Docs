---
title: AllocConsole function
description: See reference information about the AllocConsole function, which allocates a new console for the calling process.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi/AllocConsole
- wincon/AllocConsole
- AllocConsole
MS-HAID:
- '\_win32\_allocconsole'
- 'base.allocconsole'
- 'consoles.allocconsole'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: bdf3bf2f-8eb8-4ba6-bf3a-a67b29dffda2
topic_type:
- apiref
api_name:
- AllocConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
---

# AllocConsole function

Allocates a new console for the calling process.

## Syntax

```C
BOOL WINAPI AllocConsole(void);
```

## Parameters

This function has no parameters.

## Return value

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## Remarks

A process can be associated with only one console, so the **AllocConsole** function fails if the calling process already has a console. A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its current console, then it can call **AllocConsole** to create a new console or [**AttachConsole**](attachconsole.md) to attach to another console.

If the calling process creates a child process, the child inherits the new console.

**AllocConsole** initializes standard input, standard output, and standard error handles for the new console. The standard input handle is a handle to the console's input buffer, and the standard output and standard error handles are handles to the console's screen buffer. To retrieve these handles, use the [**GetStdHandle**](getstdhandle.md) function.

This function is primarily used by a graphical user interface (GUI) application to create a console window. GUI applications are initialized without a console. Console applications are initialized with a console, unless they are created as detached processes (by calling the [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) function with the **DETACHED\_PROCESS** flag).

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows 2000 Professional \[desktop apps only\] |
| Minimum supported server | Windows 2000 Server \[desktop apps only\] |
| Header | ConsoleApi.h (via WinCon.h, include Windows.h) |
| Library | Kernel32.lib |
| DLL | Kernel32.dll |

## See also

[Console Functions](console-functions.md)

[Consoles](consoles.md)

[**AllocConsoleWithOptions**](allocconsolewithoptions.md)

[**AttachConsole**](attachconsole.md)

[**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa)

[**FreeConsole**](freeconsole.md)

[**GetStdHandle**](getstdhandle.md)
