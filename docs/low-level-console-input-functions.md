---
title: Low-Level Console Input Functions
description: A low-level console input functions buffer contains input records that can include information about keyboard, mouse, buffer-resizing, focus, and menu events.
author: bitcrazed
ms.author: richturn
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- '\_win32\_low\_level\_console\_input\_functions'
- 'base.low\_level\_console\_input\_functions'
- 'consoles.low\_level\_console\_input\_functions'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 41488614-ca7c-4207-b706-f7776423c7ba
---

# Low-Level Console Input Functions


A low-level console input functions buffer contains input records that can include information about keyboard, mouse, buffer-resizing, focus, and menu events. The low-level functions provide direct access to the input buffer, unlike the high-level functions that filter and process the input buffer's data, discarding all but keyboard input.

There are five low-level functions for accessing a console's input buffer:

- [**ReadConsoleInput**](readconsoleinput.md)
- [**PeekConsoleInput**](peekconsoleinput.md)
- [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md)
- [**WriteConsoleInput**](writeconsoleinput.md)
- [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md)

The [**ReadConsoleInput**](readconsoleinput.md), [**PeekConsoleInput**](peekconsoleinput.md), and [**WriteConsoleInput**](writeconsoleinput.md) functions use the [**INPUT\_RECORD**](input-record-str.md) structure to read from or write to an input buffer.

Following are descriptions of the low-level console input functions.


| Function                                                               | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [**ReadConsoleInput**](readconsoleinput.md)                           | Reads and removes input records from an input buffer. The function does not return until at least one record is available to be read. Then all available records are transferred to the buffer of the calling process until either no more records are available or the specified number of records has been read. Unread records remain in the input buffer for the next read operation. The function reports the total number of records that have been read. For an example that uses [**ReadConsoleInput**](readconsoleinput.md), see [Reading Input Buffer Events](reading-input-buffer-events.md). |
| [**PeekConsoleInput**](peekconsoleinput.md)                           | Reads without removing the pending input records in an input buffer. All available records up to the specified number are copied into the buffer of the calling process. If no records are available, the function returns immediately. The function reports the total number of records that have been read.                                                                                                                                                                                                                                                                                              |
| [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) | Determines the number of unread input records in an input buffer.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [**WriteConsoleInput**](writeconsoleinput.md)                         | Places input records into the input buffer behind any pending records in the buffer. The input buffer grows dynamically, if necessary, to hold as many records as are written. To use this function, the specified input buffer handle must have the GENERIC\_READ access right.                                                                                                                                                                                                                                                                                                                           |
| [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md)             | Discards all unread events in the input buffer. To use this function, the specified input buffer handle must have the GENERIC\_READ access right.                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
||
||
||



A thread of an application's process can perform a wait operation to wait for input to be available in an input buffer. To initiate a wait operation, specify a handle to the input buffer in a call to any of the [wait functions](https://msdn.microsoft.com/library/windows/desktop/ms687069). These functions can return when the state of one or more objects is signaled. The state of a console input handle becomes signaled when there are unread records in its input buffer. The state is reset to nonsignaled when the input buffer becomes empty. If there is no input available, the calling thread enters an efficient wait state, consuming very little processor time while waiting for the conditions of the wait operation to be satisfied.








