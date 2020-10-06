---
title: CONSOLE_READCONSOLE_CONTROL structure
description: See reference information about the CONSOLE_READCONSOLE_CONTROL structure, which contains information for a console read operation.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords: 
- consoleapi/CONSOLE_READCONSOLE_CONTROL
- wincon/CONSOLE_READCONSOLE_CONTROL
- CONSOLE_READCONSOLE_CONTROL
- consoleapi/PCONSOLE_READCONSOLE_CONTROL
- wincon/PCONSOLE_READCONSOLE_CONTROL
- PCONSOLE_READCONSOLE_CONTROL
MS-HAID:
- 'base.console\_readconsole\_control'
- 'consoles.console\_readconsole\_control'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 6a8451a6-d692-43af-88c4-972c4dc5e07c

topic_type:
- apiref
api_name:
- CONSOLE_READCONSOLE_CONTROL
api_location:
- WinCon.h
api_type:
- HeaderDef
---

# CONSOLE\_READCONSOLE\_CONTROL structure

Contains information for a console read operation.

## Syntax

```C
typedef struct _CONSOLE_READCONSOLE_CONTROL {
  ULONG nLength;
  ULONG nInitialChars;
  ULONG dwCtrlWakeupMask;
  ULONG dwControlKeyState;
} CONSOLE_READCONSOLE_CONTROL, *PCONSOLE_READCONSOLE_CONTROL;
```

## Members

**nLength**  
The size of the structure. Set this member to `sizeof(CONSOLE_READCONSOLE_CONTROL)`.

**nInitialChars**  
The number of characters to skip (and thus preserve) before writing newly read input in the buffer passed to the [**ReadConsole**](readconsole.md) function. This value must be less than the *nNumberOfCharsToRead* parameter of the **ReadConsole** function.

**dwCtrlWakeupMask**  
A user-defined control character used to signal that the read is complete.

**dwControlKeyState**  
The state of the control keys. This member can be one or more of the following values.

| Value | Meaning |
|-|-|
| **CAPSLOCK_ON** 0x0080 | The CAPS LOCK light is on. |
| **ENHANCED_KEY** 0x0100 | The key is enhanced. See [remarks](key-event-record-str.md#remarks). |
| **LEFT_ALT_PRESSED** 0x0002 | The left ALT key is pressed. |
| **LEFT_CTRL_PRESSED** 0x0008 | The left CTRL key is pressed. |
| **NUMLOCK_ON** 0x0020 | The NUM LOCK light is on. |
| **RIGHT_ALT_PRESSED** 0x0001 | The right ALT key is pressed. |
| **RIGHT_CTRL_PRESSED** 0x0004 | The right CTRL key is pressed. |
| **SCROLLLOCK_ON** 0x0040 | The SCROLL LOCK light is on. |
| **SHIFT_PRESSED** 0x0010 | The SHIFT key is pressed. |

## Requirements

| | |
|-|-|
| Minimum supported client | Windows Vista \[desktop apps only\] |
| Minimum supported server | Windows Server 2008 \[desktop apps only\] |
| Header | ConsoleApi.h (via WinCon.h, include Windows.h) |

## See also

[**ReadConsole**](readconsole.md)
