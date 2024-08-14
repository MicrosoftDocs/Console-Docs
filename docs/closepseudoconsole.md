---
title: ClosePseudoConsole function
description: See reference information about the ClosePseudoConsole function, which closes a pseudoconsole from the given handle.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api, conpty, pseudoconsole
topic_type:
- apiref
api_name:
- ClosePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
---

# ClosePseudoConsole function

Shuts down and releases resources associated with the given pseudoconsole.

## Syntax

```C
void WINAPI ClosePseudoConsole(
    _In_ HPCON hPC
);
```

## Parameters

*hPC* \[in\]  
A handle to an active pseudoconsole as opened by [CreatePseudoConsole](createpseudoconsole.md).

## Return value

*none*

## Remarks

Closing a pseudoconsole will send **CTRL_CLOSE_EVENT** to each client application that is still connected. Until the applications have disconnected they may continue writing more output. Because of this, your application is expected to either close the output pipe before calling **ClosePseudoConsole** or to continue reading from the pipe until after **ClosePseudoConsole** has returned.

> [!NOTE]
> Starting Windows 11 24H2 (build 26100) **ClosePseudoConsole** will return immediately to avoid accidental deadlocks. Earlier versions will wait indefinitely for the pseudoconsole to exit. If you need to know when all clients have disconnected, simply continue reading from the output pipe until it has been closed on you.

> [!WARNING]
> As a consequence of the above, failure to either close or drain the output pipe may cause **ClosePseudoConsole** to wait indefinitely in earlier versions of Windows. To avoid deadlocks on older versions, don't call **ClosePseudoConsole** on the same thread that you're reading the output pipe from, unless the output pipe was previously closed by you or closed on you by the pseudoconsole.

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

[**CreatePseudoConsole**](createpseudoconsole.md)

[**ResizePseudoConsole**](resizepseudoconsole.md)
