---
title: Consoles
description: A console is an interface that provides I/O to character-mode applications. This processor-independent mechanism makes it easy to port existing character-mode applications or to create new character-mode tools and applications.
MS-HAID:
- '\_win32\_consoles'
- 'base.consoles'
- 'consoles.consoles'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 16148ce6-d3be-40dd-b82e-50ea1df67c4e
keywords: ["consoles", "consoles,described"]
---

# Consoles


A *console* is an interface that provides I/O to character-mode applications. This processor-independent mechanism makes it easy to port existing character-mode applications or to create new character-mode tools and applications.

A console consists of an input buffer and one or more screen buffers. The *input buffer* contains a queue of input records, each of which contains information about an input event. The input queue always includes key-press and key-release events. It can also include mouse events (pointer movements and button presses and releases) and events during which user actions affect the size of the active screen buffer. A *screen buffer* is a two-dimensional array of character and color data for output in a console window. Any number of processes can share a console.

-   [Creation of a Console](creation-of-a-console.md)
-   [Attaching to a Console](attaching-to-a-console.md)
-   [Closing a Console](closing-a-console.md)
-   [Console Handles](console-handles.md)
-   [Console Input Buffer](console-input-buffer.md)
-   [Console Screen Buffers](console-screen-buffers.md)
-   [Window and Screen Buffer Size](window-and-screen-buffer-size.md)
-   [Console Selection](console-selection.md)
-   [Scrolling the Screen Buffer](scrolling-the-screen-buffer.md)

 

 




