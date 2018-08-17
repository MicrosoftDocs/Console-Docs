---
title: PseudoConsoles – Windows Desktop 
description: A pseudoconsole is a concept used to provide the hosting or servicing aspect of a character-mode application.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: console, character mode applications, command line applications, terminal applications, console api, conpty, pseudoconsole

---

# Pseudoconsoles

A *pseudoconsole* is a device type that allows applications to become the host for character-mode applications. 

This is in contrast to a typical console session where the operating system will create a hosting window on behalf of the character-mode application to handle graphical output and user input.

With a pseudoconsole, the hosting window is not created. The application that makes the pseudoconsole must become responsible for displaying the graphical output and collecting user input. Alternatively, the information can be relayed further to another application responsible for these activities at a later point in the chain.

This functionality is designed for third-party "terminal window" applications to exist on the platform or for redirection of character-mode activities to a remote "terminal window" session on another machine or even on another platform.

Note that the underlying console session will still be created on behalf of the application requesting the pseudoconsole. All the rules of [console sessions](consoles.md) still apply including the ability for multiple client character-mode applications to connect to the session.

To provide maximum compatibility with the existing world of  pseudoterminal functionality, the information provided over the pseudoconsole channel will always be encoded in UTF-8. This does not affect the codepage or encoding of the client applications that are attached. Translation will happen inside the pseudoconsole system as necessary.

An example for getting started can be found at [Creating a Pseudoconsole Session](creating-a-pseudoconsole-session.md).

Some additional background information on PseudoConsoles can be found at the announcement blog post: [Windows Command-Line: Introducing the Windows Pseudo Console (ConPTY)](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).
