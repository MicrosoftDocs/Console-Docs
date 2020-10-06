---
title: Windows Console and Terminal Ecosystem Roadmap
description: Provides a high-level view of the interactions between and plans for the Windows Console Host, Console APIs, Console Subsystem, and Terminal product.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, terminal, virtual terminal, console host, command-line, subsystem, roadmap, ecosystem
ms.prod: console
---

# Windows Console and Terminal Ecosystem Roadmap

This document is intended to provide a high-level overview of the Windows Console and Windows Terminal products, how they fit into the ecosystem of command-line applications across Windows and other operating systems, and a general roadmap of the products, features, and strategies that are a part of building the platform and building for this platform.

## Definitions

It is highly recommended to familiarize yourself with the [definitions](definitions.md) behind common terminology in this space before proceeding with the remainder of this document.

## Products

All of our products are now available on GitHub in our open source repository, [Microsoft/Terminal](https://github.com/microsoft/terminal).

### Windows Console Host

This is the traditional Windows user-interface for command-line applications. It handles all console API servicing called from any attached command-line application as well as the graphical user interface representation on behalf of all of those applications. It is found as `conhost.exe`, or `openconsole.exe` in its open source form. It comes with the Windows operating system and can be redistributed from the open source repository for a more up-to-date usage of the pseudoconsole infrastructure with a modern terminal application.

### Windows Terminal

This is the new Windows interface for command-line applications, intended as a first-party example of using the pseudoconsole to separate the concerns between API servicing and text-based application interfacing, much like all non-Windows platforms. It is intended to be the flagship text mode user interface for Windows and demonstrate the capabilities of the ecosystem, drive Windows development toward a unification with other platforms, and be an example of how to build a robust and complex modern application that spans the history and gamut of Windows APIs and frameworks.

## Architecture

## Roadmap

This roadmap starts with a brief history of major milestones in the console subsystem prior to 2015. It then moves into an overview of work performed since 2015 when the renewed focus on the command-line was formed in the Windows 10 era and finishes with what is intended to come next.

### Implementation

**\[1989-1990s]** The initial console host system was implemented as an emulation of the DOS environment within the Windows operating system. Its code is entangled and cooperative with the Command Prompt, `cmd.exe`, that is a representation of that DOS environemnt and shares responsibilities and privileges with that interpreter/shell. It also provides a base level of services for other command-line utilities to perform services in a CMD-like manner.

### DBCS for CJK

**\[1997-1999\]** Around this time, DBCS support ("Double-byte character set") is introduced to support CJK (Chinese, Japanese, and Korean) markets. This effort results in a bifurcation of many of the writing and reading methods inside the console to provide both "western" versions to deal with single-byte characters as well as an alternative representation for "eastern" versions where two bytes are required to represent the vast array of characters. This also included the expansion of the representation of a cell in the console environment to be either 1 or 2 cells wide, where 1 cell is narrow (taller than it is wide) and 2 cells is wide, full-width, or otherwise a square in which typical Chinese, Japanese, and Korean ideographs can be inscribed.

### Security/Isolation

**\[2005-2009\]** With the console subsystem experience running inside the critical system process, `csrss.exe`, connecting assorted client applications at varying access levels to a single super-critical and privileged process was noticed as particularly dangerous. In this era, the console subsystem was split out into client, driver, and server applications that can each run in their own context, reducing the responsibilities and privilege in each. This isolation also increased general robustness of the system as any failure in the console subsystem no longer affected other critical process functionality.

### Windows 10 User Experience Improvements

**\[2014-2016\]** After a long time of general scattered maintenance of the console subsystem by assorted teams across the organization, a new developer focused team was formed to own and drive improvements in the console. This time frame included line selection, smooth window resizing, reflowing text, copy and paste, high DPI support, and a focus on Unicode including the convergence of the split between "western" and "eastern" storage and stream manipulation algorithms.

### Virtual Terminal client

**\[2015-2017\]** With the advent of the Windows Subsystem for Linux, Microsoft efforts to improve the experience of Docker on Windows, and the adoption of OpenSSH by the PowerShell team as the premier command-line remote execution technology, the initial implementations of Virtual Terminal Sequences were introduced into the console host. This allowed the existing console to act as the terminal attached directly to those Linux-native applications in their respective environments, rendering graphical and text attributes to the display and returning user input in the appropriate dialect.

### Virtual Terminal server

**\[2018\]** Over the past twenty years, third-party alternatives for the inbox console host had arisen to offer additional developer productivity prominently centered in rich customizations and tabbed interfaces. These applications were still beholden to run and hide the console host window and attach as a secondary "client" application to scrape out buffer information in polling loops as the primary command-line client application operated. Their goal was to be a terminal, like on other platforms, but in the Windows world where terminals were not replaceable. 

In this time period, the psuedoconsole infrastructure was introduced, to permit any application in this position to launch the console host in a non-interactive mode and become the final terminal interface for the user. The main limitation in this effort was the continued compatibility promise of Windows in servicing all published Windows Console APIs for the indefinite future while providing a replacement server hosting interface that matched what is expected on all other platforms: virtual terminal sequences. As such, this effort performed the mirror image of the client phase: the pseudoconsole projects what would be displayed onto the screen as virtual terminal sequences for a delegated host and interprets replies into Windows-format input sequences for client application consumption.

### Terminal applications

**\[2019-Now\]** This era is the open source era for the console subsystem including the new Windows Terminal project. As of the Microsoft Build conference in May 2019, the entire project is on GitHub at [Microsoft/Terminal](https://github.com/microsoft/terminal). The focus now is building the Windows Terminal application on top of the refined platform for pseudoconsoles to bring a first class terminal experience directly to developers on the Windows platform.

It is intended not only as a showcase for the platform including the WinUI technology, the MSIX packaging model, and the C++/WinRT component architecture, but also as a validation of the platform itself, driving the Windows organization to open and evolve the app platform as necessary to continue to lift the productivity of developers. The Windows Terminal's unique set of power user and developer requirements drive the modern Windows platform requirements for what those markets truly need from Windows.

Inside the Windows operating system, this also includes retiring the classic console host user interface from its default position in favor of the Terminal, ConPTY, and VT sequence experience. And finally, it is intended to offer full choice over the default experience, whether it is the Windows Terminal product or any alternative terminals.

### Client support library

**\[Future\]** With the support and documentation of virtual terminal sequences on the client side, we strongly encourage Windows command-line utility developers to use VT sequences first over the classic Windows APIs to gain the benefit of a united ecosystem with all platforms. However, one significant missing piece is that other platforms have a wide array of client-side helper libraries for handling input like [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) and graphical display like [ncurses](https://invisible-island.net/ncurses/ncurses.html). This particular future road map element represents the exploration of what the ecosystem offers and how we can accelerate the adoption of VT sequences in Windows command-line applications over the classic Console API.

### Sequence Passthrough

**\[Future\]** While the combination of virtual terminal client and server implementations allows the full mixing and matching of client command-line and terminal hosting applications that speak either the classic Windows Console APIs or Virtual Terminal Sequences, there is an overhead cost to translating the world into the classic compatible Windows method and then back into the more universal VT method. Once the market is sufficiently virtual terminal sequences and UTF-8 on Windows, the conversion/interpretation job of the console host can be optionally disabled and turn into a simple API call servicer and relay from device calls to the hosting application via the psuedoconsole. This increases performance and maximizes the dialect of sequences that can be spoken between client application and the terminal enabling additional interactivity scenarios and finally bringing the Windows world into the family with all other platforms in the command-line application space.
