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
ms.localizationpriority: high
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
| **STD_INPUT_HANDLE** `((DWORD)-10)` | The standard input device. Initially, this is the console input buffer, `CONIN$`. |
| **STD_OUTPUT_HANDLE** `((DWORD)-11)` | The standard output device. Initially, this is the active console screen buffer, `CONOUT$`. |
| **STD_ERROR_HANDLE** `((DWORD)-12)` | The standard error device. Initially, this is the active console screen buffer, `CONOUT$`. |

> [!NOTE]
> The values for these constants are unsigned numbers, but are defined in the header files as a cast from a 
signed number and take advantage of the C compiler rolling them over to just under the maximum 32-bit value. When interfacing with these handles in a language that does not parse the headers and is re-defining the constants, please be aware of this constraint. As an example, `((DWORD)-10)` is actually the unsigned number `4294967286`.

## Return value

If the function succeeds, the return value is a handle to the specified device, or a redirected handle set by a previous call to [**SetStdHandle**](setstdhandle.md). The handle has **GENERIC\_READ** and **GENERIC\_WRITE** access rights, unless the application has used **SetStdHandle** to set a standard handle with lesser access.

> [!TIP]
> It is not required to dispose of this handle with [**CloseHandle**](/windows/win32/api/handleapi/nf-handleapi-closehandle) when done. See [**Remarks**](#handle-disposal) for more information.

If the function fails, the return value is **INVALID\_HANDLE\_VALUE**. To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

If an application does not have associated standard handles, such as a service running on an interactive desktop, and has not redirected them, the return value is **NULL**.

## Remarks

Handles returned by **GetStdHandle** can be used by applications that need to read from or write to the console. When a console is created, the standard input handle is a handle to the console's input buffer, and the standard output and standard error handles are handles of the console's active screen buffer. These handles can be used by the [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) and [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) functions, or by any of the console functions that access the console input buffer or a screen buffer (for example, the [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md), or [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) functions).

The standard handles of a process may be redirected by a call to [**SetStdHandle**](setstdhandle.md), in which case **GetStdHandle** returns the redirected handle. If the standard handles have been redirected, you can specify the `CONIN$` value in a call to the [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) function to get a handle to a console's input buffer. Similarly, you can specify the `CONOUT$` value to get a handle to a console's active screen buffer.

The standard handles of a process on entry of the main method are dictated by the configuration of the [**/SUBSYSTEM**](/cpp/build/reference/subsystem-specify-subsystem) flag passed to the linker when the application was built. Specifying **/SUBSYSTEM:CONSOLE** requests that the operating system fill the handles with a console session on startup, if the parent didn't already fill the standard handle table by inheritance. On the contrary, **/SUBSYSTEM:WINDOWS** implies that the application does not need a console and will likely not be making use of the standard handles. More information on handle inheritance can be found in the documentation for [**STARTF\_USESTDHANDLES**](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa).

Some applications operate outside the boundaries of their declared subsystem; for instance, a **/SUBSYSTEM:WINDOWS** application might check/use standard handles for logging or debugging purposes but operate normally with a graphical user interface. These applications will need to carefully probe the state of standard handles on startup and make use of [**AttachConsole**](attachconsole.md), [**AllocConsole**](allocconsole.md), and [**FreeConsole**](freeconsole.md) to add/remove a console if desired.

Some applications may also vary their behavior on the type of inherited handle. Disambiguating the type between console, pipe, file, and others can be performed with [**GetFileType**](/windows/win32/api/fileapi/nf-fileapi-getfiletype).

### Handle disposal

It is not required to [**CloseHandle**](/windows/win32/api/handleapi/nf-handleapi-closehandle) when done with the handle retrieved from **GetStdHandle**. The returned value is simply a copy of the value stored in the process table. The process itself is generally considered the owner of these handles and their lifetime. It is placed in the table on creation depending on the inheritance and launch specifics of the [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw) call and will be freed when the process is destroyed.

The case to manipulate the lifetime of these handles manually with **CloseHandle** is if intentionally trying to replace or block other parts of the process from using these handles going forward. `HANDLE` is a numerical value, so another thread storing it locally will not necessarily be updated when the value from the table is updated with **SetStdHandle**. Closing the value will close it process wide and the next usage of the stored copy will encounter an error on **ReadFile** or **WriteFile** accordingly.

Guidance for replacing a standard handle in the process table would be to get the existing `HANDLE` from the table with **GetStdHandle**, use **SetStdHandle** to place a new `HANDLE` in that is opened with **CreateFile** (or a similar function), then to close the retrieved handle.

There is no validation of the values stored as handles in the process table by either the **GetStdHandle** or **SetStdHandle** functions. Validation is performed at the time of the actual read/write operation such as **ReadFile** or **WriteFile**.

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

[**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile)

[**SetStdHandle**](setstdhandle.md)

[**WriteConsole**](writeconsole.md)

[**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile)