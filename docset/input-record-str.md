---
title: INPUT\_RECORD structure
description: Describes an input event in the console input buffer.
MS-HAID:
- '\_win32\_input\_record\_str'
- 'base.input\_record\_str'
- 'consoles.input\_record\_str'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: a46ba7fd-097a-455d-96ac-13aa01e11dc1
keywords: ["INPUT_RECORD structure Consoles"]
topic_type:
- apiref
api_name:
- INPUT_RECORD
api_location:
- Wincon.h
api_type:
- HeaderDef
---

# INPUT\_RECORD structure


Describes an input event in the console input buffer. These records can be read from the input buffer by using the [**ReadConsoleInput**](readconsoleinput.md) or [**PeekConsoleInput**](peekconsoleinput.md) function, or written to the input buffer by using the [**WriteConsoleInput**](writeconsoleinput.md) function.

Syntax
------

```ManagedCPlusPlus
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

Members
-------

**EventType**  
A handle to the type of input event and the event record stored in the **Event** member.

This member can be one of the following values.

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
<td><span id="FOCUS_EVENT"></span><span id="focus_event"></span>
<strong>FOCUS_EVENT</strong>
0x0010</td>
<td><p>The <strong>Event</strong> member contains a [<strong>FOCUS_EVENT_RECORD</strong>](focus-event-record-str.md) structure. These events are used internally and should be ignored.</p></td>
</tr>
<tr class="even">
<td><span id="KEY_EVENT"></span><span id="key_event"></span>
<strong>KEY_EVENT</strong>
0x0001</td>
<td><p>The <strong>Event</strong> member contains a [<strong>KEY_EVENT_RECORD</strong>](key-event-record-str.md) structure with information about a keyboard event.</p></td>
</tr>
<tr class="odd">
<td><span id="MENU_EVENT"></span><span id="menu_event"></span>
<strong>MENU_EVENT</strong>
0x0008</td>
<td><p>The <strong>Event</strong> member contains a [<strong>MENU_EVENT_RECORD</strong>](menu-event-record-str.md) structure. These events are used internally and should be ignored.</p></td>
</tr>
<tr class="even">
<td><span id="MOUSE_EVENT"></span><span id="mouse_event"></span>
<strong>MOUSE_EVENT</strong>
0x0002</td>
<td><p>The <strong>Event</strong> member contains a [<strong>MOUSE_EVENT_RECORD</strong>](mouse-event-record-str.md) structure with information about a mouse movement or button press event.</p></td>
</tr>
<tr class="odd">
<td><span id="WINDOW_BUFFER_SIZE_EVENT"></span><span id="window_buffer_size_event"></span>
<strong>WINDOW_BUFFER_SIZE_EVENT</strong>
0x0004</td>
<td><p>The <strong>Event</strong> member contains a [<strong>WINDOW_BUFFER_SIZE_RECORD</strong>](window-buffer-size-record-str.md) structure with information about the new size of the console screen buffer.</p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

**Event**  
The event information. The format of this member depends on the event type specified by the **EventType** member.

Examples
--------

For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).

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
</tbody>
</table>

## <span id="see_also"></span>See also


[**FOCUS\_EVENT\_RECORD**](focus-event-record-str.md)

[**KEY\_EVENT\_RECORD**](key-event-record-str.md)

[**MENU\_EVENT\_RECORD**](menu-event-record-str.md)

[**MOUSE\_EVENT\_RECORD**](mouse-event-record-str.md)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**WriteConsoleInput**](writeconsoleinput.md)

 

 




