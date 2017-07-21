---
title: About Consoles
description: Consoles provide high-level support for simple character mode applications that interact with the user by using functions that read from standard input and write to standard output or standard error.
author: bitcrazed
ms.author: richturn
ms.topic: article
ms.prod: console
keywords: console, character mode applications, command line applications, terminal applications, console api
---

# About Character Mode Applications

Character mode (or "command-line") applications:

1. [Optionally] Read data from standard input (stdin)
2. Do "work"
3. [Optionally] Write data to standard output (stdout) or standard error (stderr)

Character mode applications communicate with the end-user through a "console" (or "terminal") application. A console converts user input from keyboard, mouse, touch-screen, pen, etc., and send it to a character mode application's stdin. A console may also display a character mode application's text output on the user's screen.

In Windows, the console is built-in and provides a rich API through which character mode applications can interact with the user.

-   [Consoles](consoles.md)
-   [Input and Output Methods](input-and-output-methods.md)
-   [Console Code Pages](console-code-pages.md)
-   [Console Control Handlers](console-control-handlers.md)
-   [Console Aliases](console-aliases.md)
-   [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md)
-   [Console Application Issues](console-application-issues.md)

 

 




