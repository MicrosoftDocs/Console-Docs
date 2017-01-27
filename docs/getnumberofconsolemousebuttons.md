---
title: GetNumberOfConsoleMouseButtons function
description: Retrieves the number of buttons on the mouse used by the current console.
author: miniksa
ms.author: miniksa
ms.assetid: 78a6a3be-b42f-4a7a-a612-b6a2019cfec2
keywords: ["GetNumberOfConsoleMouseButtons function Consoles"]
topic_type:
- apiref
api_name:
- GetNumberOfConsoleMouseButtons
api_location:
- Kernel32.dll
api_type:
- DllExport
---

# GetNumberOfConsoleMouseButtons function


Retrieves the number of buttons on the mouse used by the current console.

Syntax
------

```C++
BOOL WINAPI GetNumberOfConsoleMouseButtons(
  _Out_ LPDWORD lpNumberOfMouseButtons
);
```

Parameters
----------

*lpNumberOfMouseButtons* \[out\]  
A pointer to a variable that receives the number of mouse buttons.

Return value
------------

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

Remarks
-------

When a console receives mouse input, an [**INPUT\_RECORD**](input-record-str.md) structure containing a [**MOUSE\_EVENT\_RECORD**](mouse-event-record-str.md) structure is placed in the console's input buffer. The **dwButtonState** member of **MOUSE\_EVENT\_RECORD** has a bit indicating the state of each mouse button. The bit is 1 if the button is down and 0 if the button is up. To determine the number of bits that are significant, use **GetNumberOfConsoleMouseButtons**.

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
<td><p>Windows 2000 Professional [desktop apps only]</p></td>
</tr>
<tr class="even">
<td><p>Minimum supported server</p></td>
<td><p>Windows 2000 Server [desktop apps only]</p></td>
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

[Console Input Buffer](console-input-buffer.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**INPUT\_RECORD**](input-record-str.md)

[**MOUSE\_EVENT\_RECORD**](mouse-event-record-str.md)

 

 




