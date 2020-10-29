---
title: GenerateConsoleCtrlEvent function
description: Sends a specified signal to a console process group that shares the console associated with the calling process.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi2/GenerateConsoleCtrlEvent
- wincon/GenerateConsoleCtrlEvent
- GenerateConsoleCtrlEvent
MS-HAID:
- '\_win32\_generateconsolectrlevent'
- 'base.generateconsolectrlevent'
- 'consoles.generateconsolectrlevent'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: ed392d97-6fd0-4256-a783-bc7d27d01a10

topic_type:
- apiref
api_name:
- GenerateConsoleCtrlEvent
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
---

# GenerateConsoleCtrlEvent function

Sends a specified signal to a console process group that shares the console associated with the calling process.

## Syntax

```C
BOOL WINAPI GenerateConsoleCtrlEvent(
  _In_ DWORD dwCtrlEvent,
  _In_ DWORD dwProcessGroupId
);
```

## Parameters

*dwCtrlEvent* \[in\]  
The type of signal to be generated. This parameter can be one of the following values.

| Value | Meaning |
|-|-|
| **CTRL_C_EVENT** 0 | Generates a CTRL+C signal. This signal cannot be generated for process groups. If *dwProcessGroupId* is nonzero, this function will succeed, but the CTRL+C signal will not be received by processes within the specified process group. |
| **CTRL_BREAK_EVENT** 1 | Generates a CTRL+BREAK signal. |

*dwProcessGroupId* \[in\]  
The identifier of the process group to receive the signal. A process group is created when the **CREATE\_NEW\_PROCESS\_GROUP** flag is specified in a call to the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) function. The process identifier of the new process is also the process group identifier of a new process group. The process group includes all processes that are descendants of the root process. Only those processes in the group that share the same console as the calling process receive the signal. In other words, if a process in the group creates a new console, that process does not receive the signal, nor do its descendants.

If this parameter is zero, the signal is generated in all processes that share the console of the calling process.

## Return value

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## Remarks

**GenerateConsoleCtrlEvent** causes the control handler functions of processes in the target group to be called. All console processes have a default handler function that calls the [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) function. A console process can use the [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) function to install or remove other handler functions.

[**SetConsoleCtrlHandler**](setconsolectrlhandler.md) can also enable an inheritable attribute that causes the calling process to ignore CTRL+C signals. If **GenerateConsoleCtrlEvent** sends a CTRL+C signal to a process for which this attribute is enabled, the handler functions for that process are not called. CTRL+BREAK signals always cause the handler functions to be called.

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows 2000 Professional \[desktop apps only\] |
| Minimum supported server | Windows 2000 Server \[desktop apps only\] |
| Header | ConsoleApi2.h (via WinCon.h, include Windows.h) |
| Library | Kernel32.lib |
| DLL | Kernel32.dll |

## See also

[Console Control Handlers](console-control-handlers.md)

[Console Functions](console-functions.md)

[**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425)

[**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658)

[**SetConsoleCtrlHandler**](setconsolectrlhandler.md)
