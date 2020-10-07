---
title: ClosePseudoConsole function
description: See reference information about the ClosePseudoConsole function, which closes a pseudoconsole from the given handle.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
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

Closes a pseudoconsole from the given handle.

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

Upon closing a pseudoconsole, client applications attached to the session will be terminated as well.

A final painted frame may arrive on `hOutput` from the pseudoconsole when this API is called. It is expected that the caller will drain this information from the communication channel buffer and either present it or discard it. Failure to drain the buffer may cause the Close call to wait indefinitely until it is drained or the communication channels are broken another way.

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
