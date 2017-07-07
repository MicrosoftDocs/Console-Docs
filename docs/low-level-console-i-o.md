---
title: Low-Level Console I/O
description: The low-level console I/O functions expand an application's control over console I/O by enabling direct access to a console's input and screen buffers.
author: bitcrazed
ms.author: richturn
ms.topic: article
ms.prod: console
keywords: console, character mode applications, command line applications, terminal applications, console api
---

# Low-Level Console I/O


The low-level console I/O functions expand an application's control over console I/O by enabling direct access to a console's input and screen buffers. These functions enable an application to perform the following tasks:

-   Receive input about mouse and buffer-resizing events
-   Receive extended information about keyboard input events
-   Write input records to the input buffer
-   Read input records without removing them from the input buffer
-   Determine the number of pending events in the input buffer
-   Flush the input buffer
-   Read and write strings of Unicode or ANSI characters at a specified location in a screen buffer
-   Read and write strings of text and background color attributes at a specified screen buffer location
-   Read and write rectangular blocks of character and color data at a specified screen buffer location
-   Write a single Unicode or ANSI character, or a text and background color attribute combination, to a specified number of consecutive cells beginning at a specified screen buffer location

For more information, see the following topics:

-   [Console Modes](console-modes.md)
-   [Low-Level Console Modes](low-level-console-modes.md)
-   [Low-Level Console Input Functions](low-level-console-input-functions.md)
-   [Low-Level Console Output Functions](low-level-console-output-functions.md)

 

 




