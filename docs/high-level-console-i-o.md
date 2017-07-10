---
title: High-Level Console I/O
description: The high-level I/O functions provide a simple way to read a stream of characters from console input or to write a stream of characters to console output.
author: bitcrazed
ms.author: richturn
ms.topic: article
ms.prod: console
keywords: console, character mode applications, command line applications, terminal applications, console api
---

# High-Level Console I/O


The high-level I/O functions provide a simple way to read a stream of characters from console input or to write a stream of characters to console output. A high-level read operation gets input characters from a console's input buffer and stores them in a specified buffer. A high-level write operation takes characters from a specified buffer and writes them to a screen buffer at the current cursor location, advancing the cursor as each character is written.

High-level I/O gives you a choice between the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) functions and the [**ReadConsole**](readconsole.md) and [**WriteConsole**](writeconsole.md) functions. They are identical, except for two important differences. The console functions support the use of either Unicode characters or the ANSI character set; the file I/O functions do not support Unicode. Also, the file I/O functions can be used to access files, pipes, and serial communications devices; the console functions can only be used with console handles. This distinction is important if an application relies on standard handles that may have been redirected.

When using either set of high-level functions, an application can control the text and background colors used to display characters subsequently written to a screen buffer. An application can also use the console modes that affect high-level console I/O to enable or disable the following properties:

-   Echoing of keyboard input to the active screen buffer
-   Line input, in which a read operation does not return until the ENTER key is pressed
-   Automatic processing of keyboard input to handle carriage returns, CTRL+C, and other input details
-   Automatic processing of output to handle line wrapping, carriage returns, backspaces, and other output details

For more information, see the following topics:

-   [Console Modes](console-modes.md)
-   [High-Level Console Modes](high-level-console-modes.md)
-   [High-Level Console Input and Output Functions](high-level-console-input-and-output-functions.md)

 

 




