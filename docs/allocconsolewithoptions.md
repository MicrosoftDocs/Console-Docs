---
title: AllocConsoleWithOptions function
description: See reference information about the AllocConsoleWithOptions function, which allocates a new console for the calling process.
author: lhecker
ms.author: lhecker
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api, conpty, pseudoconsole
topic_type:
- apiref
api_name:
- AllocConsoleWithOptions
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-2.dll
- KernelBase.dll
api_type:
- DllExport
---

# AllocConsoleWithOptions function

Optionally allocates a new console for the calling process, while allowing you to specify the visibility of the new console window.

## Syntax

```C
HRESULT WINAPI AllocConsoleWithOptions(
    _In_opt_  PALLOC_CONSOLE_OPTIONS allocOptions,
    _Out_opt_ PALLOC_CONSOLE_RESULT  result
);
```

## Parameters

*allocOptions* \[in, optional\]  
A [**ALLOC\_CONSOLE\_OPTIONS**](alloc-console-options.md) structure that controls how this function allocates a window.

*result* \[out, optional\]  
Receives one of the following values:

| Value | Meaning |
|-|-|
| **ALLOC\_CONSOLE\_RESULT\_NO\_CONSOLE** 0 | No console was created, because **ALLOC\_CONSOLE\_MODE\_DEFAULT** was used and the parent process asked for none to be created. |
| **ALLOC\_CONSOLE\_RESULT\_NEW\_CONSOLE** 1 | A new console session was created as a result of this call. The resulting behavior is identical to [**AllocConsole**](allocconsole.md). |
| **ALLOC\_CONSOLE\_RESULT\_EXISTING\_CONSOLE** 2 | The process has attached itself to an existing console session, inherited by the parent process. The resulting behavior is identical to [**AttachConsole**](attachconsole.md). |

## Return value

Type: **HRESULT**

If this method succeeds, it returns **S_OK**. Otherwise, it returns an **HRESULT** error code.

## Remarks

Unlike with [**AllocConsole**](allocconsole.md) or [**AttachConsole**](attachconsole.md), calling this method when already connected to a console session does not result in an error.
The *result* parameter will be set to **ALLOC\_CONSOLE\_RESULT\_EXISTING\_CONSOLE** in that case.

A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its current console. A console is closed when the last process attached to it terminates or calls **FreeConsole**.

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows 11 24H2 (build 26100) \[desktop apps only\] |
| Minimum supported server | n/a |
| Header | ConsoleApi.h (via WinCon.h, include Windows.h) |
| Library | Kernel32.lib |
| DLL | Kernel32.dll |

## See also

[Console Functions](console-functions.md)

[Consoles](consoles.md)

[Console Allocation Policy](console-allocation-policy.md)

[**AllocConsole**](allocconsole.md)

[**AttachConsole**](attachconsole.md)

[**FreeConsole**](freeconsole.md)
