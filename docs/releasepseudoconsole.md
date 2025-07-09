---
title: ReleasePseudoConsole function
description: See reference information about the ReleasePseudoConsole function, which allows the pseudoconsole to exit once all clients have disconnected.
author: lhecker
ms.author: lhecker
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api, conpty, pseudoconsole
f1_keywords:
- consoleapi/ReleasePseudoConsole
- ReleasePseudoConsole
topic_type:
- apiref
api_name:
- ReleasePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-2.dll
- KernelBase.dll
api_type:
- DllExport
---

# ReleasePseudoConsole function

Relinquishes ownership of the `HPCON` handle to the pseudoconsole, allowing it to automatically exit once all clients have disconnected.

## Syntax

```C
HRESULT WINAPI ReleasePseudoConsole(
    _In_ HPCON hPC
);
```

## Parameters

*hPC* \[in\]
A handle to an active pseudoconsole as opened by [CreatePseudoConsole](createpseudoconsole.md).

## Return value

Type: **HRESULT**

If this method succeeds, it returns **S_OK**. Otherwise, it returns an **HRESULT** error code.
The call is not expected to fail unless the **hPC** argument is invalid in which case it returns **E_INVALIDARG**.

## Remarks

> [!WARNING]
> **ReleasePseudoConsole** does not deallocate the memory associated with the **HPCON**.
> You must still call **ClosePseudoConsole** once you're done using the **HPCON** instance.
> See [ClosePseudoConsole](closepseudoconsole.md) for important information about its correct usage.

The **HPCON** handle owned by your application keeps the pseudoconsole session alive indefinitely by default.
In previous versions of Windows, only **ClosePseudoConsole** would relinquish ownership of the **HPCON** handle.
However, it would also wait until all clients had disconnected before returning.

This resulted in two issues:
1. It was not possibly reliably detect whether all clients had disconnected.
   Simply testing whether the initially spawned console process had exited is insufficient, as it may have spawned additional processes that are still running.
2. It created a lifetime and ownership loop between the pseudoconsole and the application.
   Your application would keep the pseudoconsole session alive by holding on to the **HPCON** handle, while the pseudoconsole would keep your application alive, as you were waiting for an indication that all clients had disconnected before calling **ClosePseudoConsole**.

**ReleasePseudoConsole** solves this problem:
After calling this function, the pseudoconsole will automatically exit once all clients have disconnected.
All you need to do now is to read from or write to your output and input pipe handles until they return a failure.
This indicates that the all clients have disconnected and that the pseudoconsole has exited.
Call **ClosePseudoConsole** to release the remaining bits the **HPCON** handle is holding onto.

## Examples

For a full walkthrough on using this function to establish a pseudoconsole session, please see [Creating a Pseudoconsole Session](creating-a-pseudoconsole-session.md).

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows 11 24H2 (build 26100) \[desktop apps only\] |
| Minimum supported server | Windows Server 2025 (build 26100) |
| Header | ConsoleApi.h (via WinCon.h, include Windows.h) |
| Library | Kernel32.lib |
| DLL | Kernel32.dll |

## See also

[Pseudoconsoles](pseudoconsoles.md)

[Creating a Pseudoconsole Session](creating-a-pseudoconsole-session.md)

[**ClosePseudoConsole**](closepseudoconsole.md)
