---
title: GetStdHandle function
description: Retrieves a handle to the specified standard device (standard input, standard output, or standard error).
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- processenv/GetStdHandle
- winbase/GetStdHandle
- GetStdHandle
MS-HAID:
- '\_win32\_getstdhandle'
- 'base.getstdhandle'
- 'consoles.getstdhandle'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 23cd76e9-671a-48d0-9b82-2beda8917348

topic_type:
- apiref
api_name:
- GetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
---

# GetStdHandle function

Retrieves a handle to the specified standard device (standard input, standard output, or standard error).

## Syntax

```C
HANDLE WINAPI GetStdHandle(
  _In_ DWORD nStdHandle
);
```

## Parameters

*nStdHandle* \[in\]  
The standard device. This parameter can be one of the following values.

| Value | Meaning |
|-|-|
| **STD_INPUT_HANDLE** (DWORD) -10 | The standard input device. Initially, this is the console input buffer, `CONIN$`. |
| **STD_OUTPUT_HANDLE** (DWORD) -11 | The standard output device. Initially, this is the active console screen buffer, `CONOUT$`. |
| **STD_ERROR_HANDLE** (DWORD) -12 | The standard error device. Initially, this is the active console screen buffer, `CONOUT$`. |

## Return value

If the function succeeds, the return value is a handle to the specified device, or a redirected handle set by a previous call to [**SetStdHandle**](setstdhandle.md). The handle has **GENERIC\_READ** and **GENERIC\_WRITE** access rights, unless the application has used **SetStdHandle** to set a standard handle with lesser access.

If the function fails, the return value is **INVALID\_HANDLE\_VALUE**. To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

If an application does not have associated standard handles, such as a service running on an interactive desktop, and has not redirected them, the return value is **NULL**.

## Remarks

Handles returned by **GetStdHandle** can be used by applications that need to read from or write to the console. When a console is created, the standard input handle is a handle to the console's input buffer, and the standard output and standard error handles are handles of the console's active screen buffer. These handles can be used by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) functions, or by any of the console functions that access the console input buffer or a screen buffer (for example, the [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md), or [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) functions).

The standard handles of a process may be redirected by a call to [**SetStdHandle**](setstdhandle.md), in which case **GetStdHandle** returns the redirected handle. If the standard handles have been redirected, you can specify the `CONIN$` value in a call to the [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) function to get a handle to a console's input buffer. Similarly, you can specify the `CONOUT$` value to get a handle to a console's active screen buffer.

### Attach/detach behavior

When attaching to a new console, standard handles are always replaced with console handles unless **STARTF\_USESTDHANDLES** was specified during process creation.

If the existing value of the standard handle is **NULL**, or the existing value of the standard handle looks like a console pseudohandle, the handle is replaced with a console handle.

When a parent uses both **CREATE\_NEW\_CONSOLE** and **STARTF\_USESTDHANDLES** to create a console process, standard handles will not be replaced unless the existing value of the standard handle is **NULL** or a console pseudohandle.

> [!NOTE]
>Console processes *must* start with the standard handles filled or they will be filled automatically with appropriate handles to a new console. Graphical user interface (GUI) applications can be started without the standard handles and they will not be automatically filled.

## Examples

For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows 2000 Professional \[desktop apps only\] |
| Minimum supported server | Windows 2000 Server \[desktop apps only\] |
| Header | ProcessEnv.h (via Winbase.h, include Windows.h) |
| Library | Kernel32.lib |
| DLL | Kernel32.dll |

## See also

[Console Functions](console-functions.md)

[Console Handles](console-handles.md)

[**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**SetStdHandle**](setstdhandle.md)

[**WriteConsole**](writeconsole.md)

[**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)
