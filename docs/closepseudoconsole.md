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

Syntax
------

```C
void WINAPI ClosePseudoConsole(
    _In_ HPCON hPC 
);
```

Parameters
----------

*hPC* \[in\]  
A handle to an active psuedoconsole as opened by [CreatePseudoConsole](createpseudoconsole.md).

Return value
------------

*none*

Remarks
-------

Upon closing a pseudoconsole, client applications attached to the session will be terminated as well.

A final painted frame may arrive on `hOutput` from the pseudoconsole when this API is called. It is expected that the caller will drain this information from the communication channel buffer and either present it or discard it. Failure to drain the buffer may cause the Close call to wait indefinitely until it is drained or the communication channels are broken another way.

Requirements
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Minimum supported client</p></td>
<td><p>Windows 10 1809 [desktop apps only]</p></td>
</tr>
<tr class="even">
<td><p>Minimum supported server</p></td>
<td><p>Windows Server 2019 [desktop apps only]</p></td>
</tr>
<tr class="odd">
<td><p>Header</p></td>
<td>ConsoleApi.h (via Wincon.h, include Windows.h)</td>
</tr>
<tr class="even">
<td><p>Library</p></td>
<td>Kernel32.lib</td>
</tr>
<tr class="odd">
<td><p>DLL</p></td>
<td>Kernel32.dll</td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <span id="see_also"></span>See also

[Pseudoconsoles](pseudoconsoles.md)

[**CreatePseudoConsole**](createpseudoconsole.md)

[**ResizePseudoConsole**](resizepseudoconsole.md)
