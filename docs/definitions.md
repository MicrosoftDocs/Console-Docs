---
title: Windows Console and Terminal Definitions
description: Provides definitions of words and phrases commonly used in this space and document set related to the console and terminal system.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, terminal, virtual terminal, console host, command-line, subsystem, definitions
---

# Definitions

This document provides the definitions of specific words and phrases in this space and be used as reference throughout this document set.

## Command Line Applications

Command line applications, or sometimes called "console applications" and/or referred to as "clients" of the console subsystem, are programs that operate mainly on a stream of text or character information. They generally contain no user interface elements of their own and delegate both the output/display and the input/interaction roles to a hosting application. Command line applications receive a stream of text on their standard input `STDIN` handle which represents a user's keyboard input, process that information, then respond with a stream of text on their standard output `STDOUT` for display back to the user's monitor. Of course, this has evolved over time for additional input devices and remote scenarios, but the same basic philosophy remains the same: command-line clients operate on text and someone else manages display/input.

## Standard Handles

The standard handles are a series, `STDIN`, `STDOUT`, and `STDERR`, introduced as part of a process space on startup. They represent a place for information to be accepted on the way in and sent back on the way out (including a special place to report errors out). For command-line applications, these must always exist when the application starts. They are either inherited from the parent automatically, set explicitly by the parent, or created automatically by the operating system if neither are specified/permitted. For classic Windows applications, these may be blank on startup. However, they can be implicitly or explicitly inherited from the parent or allocated, attached, and freed during runtime by the application itself.

Standard handles do not imply a specific type of attached device. In the case of command-line applications, however, the device is most commonly a console device, file (from redirection in a shell), or a pipe (from a shell connecting the output of one utility to the input of the next). It may also be a socket or any other type of device.

## TTY/PTY

On non-Windows platforms, the TTY and PTY devices represent respectively either a true physical device or a software-created pseudo-device that are the same concept as a Windows console session: a channel where communication between a command-line client application and a server host interactivity application or physical keyboard/display device can exchange text-based information.

## Clients and Servers

Within this space, we're referring to "clients" as applications that do the work of processing information and running commands. The "server" applications are those that are responsible for the user interface and are workers to translate input and output into standard forms on behalf of the clients.

## Console Subsystem

This is a catch-all term representing all modules affecting console and command-line operations. It specifically refers to a flag that is a part of the Portable Executable header that specifies whether the starting application is either a command-line/console application (and must have standard handles to start) or a windows application (and does not need them).

The console host, command-line client applications, the console driver, the console API surface, the pseudoconsole infrastructure, terminals, configuration property sheets, the mechanisms and stubs inside the process loader, and any utilities related to the workings of these forms of applications are considered to belong to this group.

## Console Host

The Windows Console Host, or `conhost.exe`, is both the server application for all of the Windows Console APIs as well as the classic Windows user interface for working with command-line applications. The complete contents of this binary, both the API server and the UI, historically belonged to Windows `csrss.exe`, a critical system process, and was diverged for security and isolation purposes. Going forward, `conhost.exe` will continue to be responsible for API call servicing and translation, but the user-interface components are intended to be delegated through a pseudoconsole to a terminal.

## Pseudoconsole

This is the Windows simulation of a pseudoterminal or "PTY" from other platforms. It tries to match the general interface philosophy of PTYs, providing a simple bidirectional channel of text based communication, but it supplements it on Windows with a large compatibility layer to translate the breadth of Windows applications written prior to this design philosophy change from the classic console API surface into the simple text channel communication form. Terminals can use the pseudoconsole to take ownership of the user-interface elements away from the console host, `conhost.exe`, while leaving it in charge of the API servicing, translation, and compatibility efforts.

## Terminal

A terminal is the user-interface and interaction module for a command-line application. Today, it's a software representation of what used to be historically a physical device with a display monitor, a keyboard, and a bidirectional serial communication channel. It is responsible for gathering input from the user in a variety of forms, translating it and encoding it and any special command information into a single text stream, and submitting it to the PTY for transmission on to the `STDIN` channel of the command-line client application. It is also responsible for receiving back information, via the PTY, that came from a client application's `STDOUT` channel, decoding any special information in the payload, laying out all the text and additional commands, and presenting that graphically to the end user.
