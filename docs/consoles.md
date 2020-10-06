---
title: Consoles – Windows Desktop 
description: A console is an application that provides I/O to command-line applications. 
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- '\_win32\_consoles'
- 'base.consoles'
- 'consoles.consoles'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 16148ce6-d3be-40dd-b82e-50ea1df67c4e
---

# Consoles

A *console* is an application that provides I/O services to character-mode applications. This processor-independent mechanism makes it easy to port existing character-mode applications or to create new character-mode tools and applications.

A console consists of an input buffer and one or more screen buffers. The *input buffer* contains a queue of input records, each of which contains information about an input event. The input queue always includes key-press and key-release events. It may also include mouse events (pointer movements and button presses and releases) and events during which user actions affect the size of the active screen buffer. A *screen buffer* is a two-dimensional array of character and color data for output in a console window. Any number of processes can share a console.

> [!TIP]
>A broader idea of consoles and how they relate to terminals and command-line client applications can be found in the **[ecosystem roadmap](ecosystem-roadmap.md)**.

- [Creation of a Console](creation-of-a-console.md)
- [Attaching to a Console](attaching-to-a-console.md)
- [Closing a Console](closing-a-console.md)
- [Console Handles](console-handles.md)
- [Console Input Buffer](console-input-buffer.md)
- [Console Screen Buffers](console-screen-buffers.md)
- [Window and Screen Buffer Size](window-and-screen-buffer-size.md)
- [Console Selection](console-selection.md)
- [Scrolling the Screen Buffer](scrolling-the-screen-buffer.md)
