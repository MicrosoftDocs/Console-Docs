---
title: GetConsoleProcessList function
description: See reference information about the GetConsoleProcessList function, which retrieves a list of the processes attached to the current console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi3/GetConsoleProcessList
- wincon/GetConsoleProcessList
- GetConsoleProcessList
MS-HAID:
- '\_win32\_getconsoleprocesslist'
- 'base.getconsoleprocesslist'
- 'consoles.getconsoleprocesslist'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 3d21103b-662d-4393-ae3f-773cd9e4a930

topic_type:
- apiref
api_name:
- GetConsoleProcessList
api_location:
- Kernel32.dll
api_type:
- DllExport
---

# GetConsoleProcessList function

Retrieves a list of the processes attached to the current console.

## Syntax

```C
DWORD WINAPI GetConsoleProcessList(
  _Out_ LPDWORD lpdwProcessList,
  _In_  DWORD   dwProcessCount
);
```

## Parameters

*lpdwProcessList* \[out\]  
A pointer to a buffer that receives an array of process identifiers upon success. This must be a valid buffer and cannot be `NULL`. The buffer must have space to receive at least 1 returned process id.

*dwProcessCount* \[in\]  
The maximum number of process identifiers that can be stored in the *lpdwProcessList* buffer. This must be greater than 0.

## Return value

If the function succeeds, the return value is less than or equal to *dwProcessCount* and represents the number of process identifiers stored in the *lpdwProcessList* buffer.

If the buffer is too small to hold all the valid process identifiers, the return value is the required number of array elements. The function will have stored no identifiers in the buffer. In this situation, use the return value to allocate a buffer that is large enough to store the entire list and call the function again.

If the return value is zero, the function has failed, because every console has at least one process associated with it. To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

If a `NULL` process list was provided or the process count was 0, the call will return 0 and `GetLastError` will return `ERROR_INVALID_PARAMETER`. Please provide a buffer of at least one element to call this function. Allocate a larger buffer and call again if the return code is larger than the length of the provided buffer.

## Remarks

To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later. For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).

[!INCLUDE [no-vt-equiv-local-context](./includes/no-vt-equiv-local-context.md)]

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows XP \[desktop apps only\] |
| Minimum supported server | Windows Server 2003 \[desktop apps only\] |
| Header | ConsoleApi3.h (via WinCon.h, include Windows.h) |
| Library | Kernel32.lib |
| DLL | Kernel32.dll |

## See also

[**AttachConsole**](attachconsole.md)

[Console Functions](console-functions.md)