---
title: SetStdHandle function
description: Sets the handle for the specified standard device (standard input, standard output, or standard error).
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- processenv/SetStdHandle
- winbase/SetStdHandle
- SetStdHandle
MS-HAID:
- '\_win32\_setstdhandle'
- 'base.setstdhandle'
- 'consoles.setstdhandle'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: f5952460-1839-415e-b400-2f04425f288a

topic_type:
- apiref
api_name:
- SetStdHandle
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

# SetStdHandle function

Sets the handle for the specified standard device (standard input, standard output, or standard error).

## Syntax

```cpp
BOOL WINAPI SetStdHandle(
  _In_ DWORD  nStdHandle,
  _In_ HANDLE hHandle
);
```

## Parameters

*nStdHandle* \[in\]  
The standard device for which the handle is to be set. This parameter can be one of the following values.

| Value | Meaning |
|-|-|
| **STD_INPUT_HANDLE** `((DWORD)-10)` | The standard input device. Initially, this is the console input buffer, `CONIN$`. |
| **STD_OUTPUT_HANDLE** `((DWORD)-11)` | The standard output device. Initially, this is the active console screen buffer, `CONOUT$`. |
| **STD_ERROR_HANDLE** `((DWORD)-12)` | The standard error device. Initially, this is the active console screen buffer, `CONOUT$`. |

> [!NOTE]
> The values for these constants are unsigned numbers, but are defined in the header files as a cast from a 
signed number and take advantage of the C compiler rolling them over to just under the maximum 32-bit value. When interfacing with these handles in a language that does not parse the headers and is re-defining the constants, please be aware of this constraint. As an example, `((DWORD)-10)` is actually the unsigned number `4294967286`.

*hHandle* \[in\]  
The handle for the standard device.

## Return value

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## Remarks

The standard handles of a process may have been redirected by a call to **SetStdHandle**, in which case [**GetStdHandle**](getstdhandle.md) will return the redirected handle. If the standard handles have been redirected, you can specify the CONIN$ value in a call to the [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) function to get a handle to a console's input buffer. Similarly, you can specify the CONOUT$ value to get a handle to the console's active screen buffer.

## Examples

For an example, see [Creating a Child Process with Redirected Input and Output](/windows/win32/procthread/creating-a-child-process-with-redirected-input-and-output).

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

[**GetStdHandle**](getstdhandle.md)