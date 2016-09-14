---
title: CONSOLE\_READCONSOLE\_CONTROL structure
description: Contains information for a console read operation.
MS-HAID:
- 'base.console\_readconsole\_control'
- 'consoles.console\_readconsole\_control'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 6a8451a6-d692-43af-88c4-972c4dc5e07c
keywords: ["CONSOLE_READCONSOLE_CONTROL structure Consoles", "PCONSOLE_READCONSOLE_CONTROL structure pointer Consoles"]
topic_type:
- apiref
api_name:
- CONSOLE_READCONSOLE_CONTROL
api_location:
- Wincon.h
api_type:
- HeaderDef
---

# CONSOLE\_READCONSOLE\_CONTROL structure


Contains information for a console read operation.

Syntax
------

```ManagedCPlusPlus
typedef struct _CONSOLE_READCONSOLE_CONTROL {
  ULONG nLength;
  ULONG nInitialChars;
  ULONG dwCtrlWakeupMask;
  ULONG dwControlKeyState;
} CONSOLE_READCONSOLE_CONTROL, *PCONSOLE_READCONSOLE_CONTROL;
```

Members
-------

**nLength**  
The size of the structure. Set this member to `sizeof(CONSOLE_READCONSOLE_CONTROL)`.

**nInitialChars**  
The number of characters to skip (and thus preserve) before writing newly read input in the buffer passed to the [**ReadConsole**](readconsole.md) function. This value must be less than the *nNumberOfCharsToRead* parameter of the **ReadConsole** function.

**dwCtrlWakeupMask**  
A user-defined control character used to signal that the read is complete.

**dwControlKeyState**  
The state of the control keys. This member can be one or more of the following values.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Value</th>
<th>Meaning</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="" id="capslock-on"></a>
<strong>CAPSLOCK_ON</strong>
0x0080</td>
<td><p>The CAPS LOCK light is on.</p></td>
</tr>
<tr class="even">
<td><a href="" id="enhanced-key"></a>
<strong>ENHANCED_KEY</strong>
0x0100</td>
<td><p>The key is enhanced.</p></td>
</tr>
<tr class="odd">
<td><a href="" id="left-alt-pressed"></a>
<strong>LEFT_ALT_PRESSED</strong>
0x0002</td>
<td><p>The left ALT key is pressed.</p></td>
</tr>
<tr class="even">
<td><a href="" id="left-ctrl-pressed"></a>
<strong>LEFT_CTRL_PRESSED</strong>
0x0008</td>
<td><p>The left CTRL key is pressed.</p></td>
</tr>
<tr class="odd">
<td><a href="" id="numlock-on"></a>
<strong>NUMLOCK_ON</strong>
0x0020</td>
<td><p>The NUM LOCK light is on.</p></td>
</tr>
<tr class="even">
<td><a href="" id="right-alt-pressed"></a>
<strong>RIGHT_ALT_PRESSED</strong>
0x0001</td>
<td><p>The right ALT key is pressed.</p></td>
</tr>
<tr class="odd">
<td><a href="" id="right-ctrl-pressed"></a>
<strong>RIGHT_CTRL_PRESSED</strong>
0x0004</td>
<td><p>The right CTRL key is pressed.</p></td>
</tr>
<tr class="even">
<td><a href="" id="scrolllock-on"></a>
<strong>SCROLLLOCK_ON</strong>
0x0040</td>
<td><p>The SCROLL LOCK light is on.</p></td>
</tr>
<tr class="odd">
<td><a href="" id="shift-pressed"></a>
<strong>SHIFT_PRESSED</strong>
0x0010</td>
<td><p>The SHIFT key is pressed.</p></td>
</tr>
</tbody>
</table>

 

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
<td><p>Windows Vista [desktop apps only]</p></td>
</tr>
<tr class="even">
<td><p>Minimum supported server</p></td>
<td><p>Windows Server 2008 [desktop apps only]</p></td>
</tr>
<tr class="odd">
<td><p>Header</p></td>
<td>Wincon.h</td>
</tr>
</tbody>
</table>

## See also


[**ReadConsole**](readconsole.md)

 

 




