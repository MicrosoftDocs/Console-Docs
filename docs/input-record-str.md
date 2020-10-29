---
title: INPUT_RECORD structure
description: See reference information about the INPUT_RECORD structure, which describes an input event in the console input buffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- wincontypes/INPUT_RECORD
- wincon/INPUT_RECORD
- INPUT_RECORD
- wincontypes/PINPUT_RECORD
- wincon/PINPUT_RECORD
- PINPUT_RECORD
MS-HAID:
- '\_win32\_input\_record\_str'
- 'base.input\_record\_str'
- 'consoles.input\_record\_str'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: a46ba7fd-097a-455d-96ac-13aa01e11dc1

topic_type:
- apiref
api_name:
- INPUT_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
---

# INPUT\_RECORD structure

Describes an input event in the console input buffer. These records can be read from the input buffer by using the [**ReadConsoleInput**](readconsoleinput.md) or [**PeekConsoleInput**](peekconsoleinput.md) function, or written to the input buffer by using the [**WriteConsoleInput**](writeconsoleinput.md) function.

## Syntax

```C
typedef struct _INPUT_RECORD {
  WORD  EventType;
  union {
    KEY_EVENT_RECORD          KeyEvent;
    MOUSE_EVENT_RECORD        MouseEvent;
    WINDOW_BUFFER_SIZE_RECORD WindowBufferSizeEvent;
    MENU_EVENT_RECORD         MenuEvent;
    FOCUS_EVENT_RECORD        FocusEvent;
  } Event;
} INPUT_RECORD;
```

## Members

**EventType**  
A handle to the type of input event and the event record stored in the **Event** member.

This member can be one of the following values.

| Value | Meaning |
|-|-|
| **FOCUS_EVENT** 0x0010 | The **Event** member contains a **[FOCUS_EVENT_RECORD](focus-event-record-str.md)** structure. These events are used internally and should be ignored. |
| **KEY_EVENT** 0x0001 | The **Event** member contains a **[KEY_EVENT_RECORD](key-event-record-str.md)** structure with information about a keyboard event. |
| **MENU_EVENT** 0x0008 | The **Event** member contains a **[MENU_EVENT_RECORD](menu-event-record-str.md)** structure. These events are used internally and should be ignored. |
| **MOUSE_EVENT** 0x0002 | The **Event** member contains a **[MOUSE_EVENT_RECORD](mouse-event-record-str.md)** structure with information about a mouse movement or button press event. |
| **WINDOW_BUFFER_SIZE_EVENT** 0x0004 | The **Event** member contains a **[WINDOW_BUFFER_SIZE_RECORD](window-buffer-size-record-str.md)** structure with information about the new size of the console screen buffer. |

**Event**  
The event information. The format of this member depends on the event type specified by the **EventType** member.

## Examples

For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows 2000 Professional \[desktop apps only\] |
| Minimum supported server | Windows 2000 Server \[desktop apps only\] |
| Header | WinConTypes.h (via WinCon.h, include Windows.h) |

## See also

[**FOCUS\_EVENT\_RECORD**](focus-event-record-str.md)

[**KEY\_EVENT\_RECORD**](key-event-record-str.md)

[**MENU\_EVENT\_RECORD**](menu-event-record-str.md)

[**MOUSE\_EVENT\_RECORD**](mouse-event-record-str.md)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**WriteConsoleInput**](writeconsoleinput.md)
