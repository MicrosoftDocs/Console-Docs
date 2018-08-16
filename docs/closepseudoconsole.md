---
title: ClosePseudoConsole function
description: Closes a pseudoconsole from the given handle
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
HRESULT WINAPI ClosePseudoConsole(
    _In_ HPCON hPC 
);
```

Parameters
----------

*hPC* \[in\]
A handle to an active psuedoconsole as opened by [CreatePseudoConsole](createpseudoconsole.md).

Return value
------------

Type: **HRESULT**

If this method succeeds, it returns **S_OK**. Otherwise, it returns an **HRESULT** error code.

Remarks
-------

Upon closing a pseudoconsole, client applications attached to the session will be terminated as well.

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
<td><p>Windows 10 RS5 [desktop apps only]</p></td>
</tr>
<tr class="even">
<td><p>Minimum supported server</p></td>
<td><p>Windows Server 2019 [desktop apps only]</p></td>
</tr>
<tr class="odd">
<td><p>Header</p></td>
<td>Wincon.h (include Windows.h)</td>
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


[Console Functions](console-functions.md)

[PseudoConsoles](pseudoconsoles.md)

[**CreatePseudoConsole**](createpsuedoconsole.md)

[**ResizePseudoConsole**](resizepseudoconsole.md)
