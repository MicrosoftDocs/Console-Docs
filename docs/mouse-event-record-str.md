---
title: MOUSE_EVENT_RECORD structure
description: See reference information about the MOUSE_EVENT_RECORD structure, which describes a mouse input event in a console INPUT_RECORD structure.
author: miniksa
ms.author: miniksa
ms.topic: reference
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- wincontypes/MOUSE_EVENT_RECORD
- wincon/MOUSE_EVENT_RECORD
- MOUSE_EVENT_RECORD
- wincontypes/PMOUSE_EVENT_RECORD
- wincon/PMOUSE_EVENT_RECORD
- PMOUSE_EVENT_RECORD
MS-HAID:
- '\_win32\_mouse\_event\_record\_str'
- 'base.mouse\_event\_record\_str'
- 'consoles.mouse\_event\_record\_str'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 84ea54c6-8872-4111-8d72-1377409b9247

topic_type:
- apiref
api_name:
- MOUSE_EVENT_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
---

# MOUSE\_EVENT\_RECORD structure

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Describes a mouse input event in a console [**INPUT\_RECORD**](input-record-str.md) structure.

## Syntax

```C
typedef struct _MOUSE_EVENT_RECORD {
  COORD dwMousePosition;
  DWORD dwButtonState;
  DWORD dwControlKeyState;
  DWORD dwEventFlags;
} MOUSE_EVENT_RECORD;
```

## Members

**dwMousePosition**  
A [**COORD**](coord-str.md) structure that contains the location of the cursor, in terms of the console screen buffer's character-cell coordinates.

**dwButtonState**  
The status of the mouse buttons. The least significant bit corresponds to the leftmost mouse button. The next least significant bit corresponds to the rightmost mouse button. The next bit indicates the next-to-leftmost mouse button. The bits then correspond left to right to the mouse buttons. A bit is 1 if the button was pressed.

The following constants are defined for the first five mouse buttons.

| Value | Meaning |
|-|-|
| **FROM_LEFT_1ST_BUTTON_PRESSED** 0x0001 | The leftmost mouse button. |
| **FROM_LEFT_2ND_BUTTON_PRESSED** 0x0004 | The second button fom the left. |
| **FROM_LEFT_3RD_BUTTON_PRESSED** 0x0008 | The third button from the left. |
| **FROM_LEFT_4TH_BUTTON_PRESSED** 0x0010 | The fourth button from the left. |
| **RIGHTMOST_BUTTON_PRESSED** 0x0002 | The rightmost mouse button. |

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

**dwEventFlags**  
The type of mouse event. If this value is zero, it indicates a mouse button being pressed or released. Otherwise, this member is one of the following values.

| Value | Meaning |
|-|-|
| **DOUBLE_CLICK** 0x0002 | The second click (button press) of a double-click occurred. The first click is returned as a regular button-press event. |
| **MOUSE_HWHEELED** 0x0008 | The horizontal mouse wheel was moved.<br /><br />If the high word of the **dwButtonState** member contains a positive value, the wheel was rotated to the right. Otherwise, the wheel was rotated to the left. |
| **MOUSE_MOVED** 0x0001 | A change in mouse position occurred. |
| **MOUSE_WHEELED** 0x0004 | The vertical mouse wheel was moved.<br /><br />If the high word of the **dwButtonState** member contains a positive value, the wheel was rotated forward, away from the user. Otherwise, the wheel was rotated backward, toward the user. |

## Remarks

Mouse events are placed in the input buffer when the console is in mouse mode (**ENABLE\_MOUSE\_INPUT**).

Mouse events are generated whenever the user moves the mouse, or presses or releases one of the mouse buttons. Mouse events are placed in a console's input buffer only when the console group has the keyboard focus and the cursor is within the borders of the console's window.

## Examples

For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows 2000 Professional \[desktop apps only\] |
| Minimum supported server | Windows 2000 Server \[desktop apps only\] |
| Header | WinConTypes.h (via WinCon.h, include Windows.h) |

## See also

[**COORD**](coord-str.md)

[**INPUT\_RECORD**](input-record-str.md)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**WriteConsoleInput**](writeconsoleinput.md)
