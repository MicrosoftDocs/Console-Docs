---
title: ResizePseudoConsole function
description: See reference information about the ResizePseudoConsole function, which resizes the internal buffers for a pseudoconsole to the given size.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: windows
keywords: console, character mode applications, command line applications, terminal applications, console api, conpty, pseudoconsole
f1_keywords:
- consoleapi/ResizePseudoConsole
- ResizePseudoConsole
topic_type:
- apiref
api_name:
- ResizePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
---

# ResizePseudoConsole function

Resizes the internal buffers for a pseudoconsole to the given size.

## Syntax

```C
HRESULT WINAPI ResizePseudoConsole(
    _In_ HPCON hPC ,
    _In_ COORD size
);
```

## Parameters

*hPC* \[in\]  
A handle to an active pseudoconsole as opened by [CreatePseudoConsole](createpseudoconsole.md).

*size* \[in\]  
The dimensions of the window/buffer in count of characters that will be used for the internal buffer of this pseudoconsole.

## Return value

Type: **HRESULT**

If this method succeeds, it returns **S_OK**. Otherwise, it returns an **HRESULT** error code.

## Remarks

This function can resize the internal buffers in the pseudoconsole session to match the window/buffer size being used for display on the terminal end. This ensures that attached Command-Line Interface (CUI) applications using the [Console Functions](console-functions.md) to communicate will have the correct dimensions returned in their calls.

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

[**ClosePseudoConsole**](closepseudoconsole.md)
