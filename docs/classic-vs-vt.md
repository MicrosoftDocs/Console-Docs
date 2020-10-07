---
title: Classic Console APIs versus Virtual Terminal Sequences
description: Describes the contrast between the classic Win32 console API surface and the concept of virtual terminal sequences, sometimes also known as escape sequences, to write command-line applications.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, terminal, virtual terminal, escape sequences, vt, vt100, console api
ms.prod: console

---

# Classic Console APIs versus Virtual Terminal Sequences

This article will discuss the difference between the classic Windows Console API surface, defined as the series of C language functional interfaces on `kernel32.dll` with "Console" in the name, and [Virtual Terminal Sequences](console-virtual-terminal-sequences.md), defined as a language of commands embedded in the standard input and standard output streams utilizing non-printable escape characters for signaling commands interleaved with normal printable text.

## History

The Windows Console has provided a broad API surface for client command-line applications to manipulate both the output display buffer and the user input buffer. However, other non-Windows platforms have never afforded this specific API-driven approach to their command-line environments, choosing instead to use virtual terminal sequences embedded within the standard input and standard output streams. For a time, Microsoft supported this behavior too in early editions of DOS and Windows through a driver called ANSI.SYS.

By contrast, all other platforms derive their command-line environment operations from various dialects of virtual terminal sequences. These sequences are rooted in an [ECMA Standard](https://www.ecma-international.org/publications/standards/Ecma-048.htm) and series of extensions by many vendors tracing back to Digital Equipment Corporation and Tektronix terminals through more modern and common software terminals like [xterm](https://invisible-island.net/xterm/). Many extensions exist within the virtual terminal sequence domain and some sequences are more widely supported than others, but it is safe to say that the world has standardized on this as the command language for command-line experiences with a well-known subset being supported by virtually every terminal and command-line client application.

## Comparisons

### Cross-Platform Support

As every platform in the world, except Windows, natively spoke virtual terminal sequences, both terminal applications and command-line utilities have been easily portable between versions and variations of those operating systems. By contrast, Windows APIs are only supported on Windows. An extensive adapter or translation library has to be written between Windows and VT or vice versa when attempting to port command-line utilities from one platform or another.

### Remote Access

Virtual Terminal Sequences hold a major advantage for remote access as they require no additional work to transport or perform remote procedure calls over what is required to set up a standard remote command-line connection. Simply connecting an outbound and an inbound transport channel (or a single bidirectional channel) over a pipe, socket, file, serial port, or any other device is sufficient to completely carry all information required for an application speaking these sequences to a remote host. On the contrary, the Windows Console APIs have only been accessible on the local machine and all efforts to remote them would require building an entire remote calling and transport interface layer beyond just a simple channel.

### Separation of Concerns

Some of the Windows Console APIs provide low-level access to the input and output buffers or convenience functions for interactive command-lines like aliases and command history programmed within the console subsystem and host environment, instead of within the command-line client application itself. This is in contrast to other platforms where both the memory of the current state of the application and convenience functionality is the responsibility of the command-line utility or shell itself.

While the Windows way of handling this responsibility in the console host and API makes it quicker and easier to write a command-line application with these features and without responsibility of remembering drawing state or handling editing convenience features, it makes it nearly impossible to connect those activities remotely across platforms, versions, or scenarios due to variations in implementations and availability. It also makes the final interactive experience of these Windows command-line applications completely dependent on the console host's implementation, priorities, and release cycle. 

For example, advanced line editing features like syntax highlighting and complex selection are only possible when a command-line application handles editing concerns itself. The console could never have enough context to fully understand these scenarios in a broad manner like the client application can.

By contrast, other platforms handle these activities and virtual terminal communication itself through reusable client-side libraries like [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) and [ncurses](https://invisible-island.net/ncurses/ncurses.html). The final terminal is only responsible for displaying information and receiving input through that bidirectional communication channel.

### Wrong-Way Verbs

On Windows, some actions can be performed in the opposite-to-natural direction on the input and output streams. This allows Windows command-line applications to both avoid the concern of managing their own buffers and to perform advanced operations like simulating/injecting input on behalf of a user or reading back some of the history of what was written. While this provides additional power to Windows applications operating in a specific user context on a single machine, it also provides a vector to cross security and privilege levels or domains when used in scenarios between contexts on the same machine or even across contexts to another machine or environment. Other platforms do not allow this activity and our intent is to converge with that strategy for both interoperability and security reasons.

### Direct Window Access

On Windows, the exact window handle to the hosting window is available through the Console API surface. This allows a command-line utility to perform advanced window operations by reaching into the wide gamut of Win32 APIs permitted against a window handle and manipulate the window state, frame, icon, or other properties about the window. By contrast, on other platforms with virtual terminal sequences, there is a narrow set of commands that can be performed against the window to do things like changing its size or displayed title and they must be done in the same band and under the same control as the remainder of the stream.

As Windows has evolved, the security controls and restrictions on window handles have increased. Additionally, the nature and existence of an application-addressable window handle on any specific user interface element has evolved, especially with the increased support of device form factors and platforms. This makes direct window access to command-line applications fragile as the platform and experiences evolve.

### Unicode

The implicit standard for communication across platforms and the web is Unicode, specifically in the UTF-8 form. Of course, other encodings still exist.  However, when otherwise undefined, using UTF-8 is widely accepted as the appropriate default. It represents the balance of portability, storage/transmission size, and breadth of expression required to support the world's languages and glyphs.

The Windows console platform has supported and will continue to support all existing code pages and encodings, but we recommend UTF-8 for all forward looking development and also accept UTF-16 as an algorithmically-translatable alternative.

UTF-8 support in the console can be found via the _A_ variant of all Console APIs against console handles after setting the codepage to `65001` or `CP_UTF8` with the [**SetConsoleOutputCP**](setconsoleoutputcp.md) and [**SetConsoleCP**](setconsolecp.md) methods as appropriate. Setting the code pages in advance is only necessary if the machine has not chosen "Use Unicode UTF-8 for worldwide language support" in the settings for Non-Unicode applications in the Region section of the Control Panel.

UTF-16 support in the console can be utilized with no additional configuration via the _W_ variant of all console APIs and is a more likely choice for applications already well versed in UTF-16 through communication with the `wchar_t` and _W_ variant of other Microsoft and Windows platform functions and products.

## Recommendations

For all new and ongoing development on Windows, virtual terminal sequences are recommended as the way of interacting with the terminal. This will converge Windows command-line client applications with the style of application programming on all other platforms.

A limited subset of Windows Console APIs is still necessary to establish the initial environment as the Windows platform still differs from others in process, signal, device, and encoding handling:

- The standard handles to a process will still be controlled with **[GetStdHandle](getstdhandle.md)** and **[SetStdHandle](setstdhandle.md)**.
- Configuration of the console modes on a handle to opt in to Virtual Terminal Sequence support will be handled with **[GetConsoleMode](getconsolemode.md)** and **[SetConsoleMode](setconsolemode.md)**.
- Declaration of code page or UTF-8 support is conducted with [**SetConsoleOutputCP**](setconsoleoutputcp.md) and [**SetConsoleCP**](setconsolecp.md) methods.
- Some level of overall process management may be required with the [**AllocConsole**](allocconsole.md), [**AttachConsole**](attachconsole.md) and [**FreeConsole**](freeconsole.md) to join or leave a console device session.
- Signals and signal handling will continue to be conducted with [**SetConsoleCtrlHandler**](setconsolectrlhandler.md), [**HandlerRoutine**](handlerroutine.md), and [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md).
- Communication with the console device handles can be conducted with [**WriteConsole**](writeconsole.md) and [**ReadConsole**](readconsole.md).
    - These may also be leveraged through programming language runtimes in the forms of:
        - C Runtime (CRT): [Stream I/O](https://docs.microsoft.com/cpp/c-runtime-library/stream-i-o) like **printf**, **scanf**, **putc**, **getc**, or [other levels of I/O functions](https://docs.microsoft.com/cpp/c-runtime-library/input-and-output).
        - C++ Standard Library (STL): [iostream](https://docs.microsoft.com/cpp/standard-library/iostream) like **cout** and **cin**.
        - .NET Runtime: [System.Console](https://docs.microsoft.com/dotnet/api/system.console) like **Console.WriteLine**.
    - Applications that must be aware of window size changes will still need to use [**ReadConsoleInput**](readconsoleinput.md) to receive them interleaved with key events as **ReadConsole** alone will discard them.
- Finding the window size must still be performed with [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) for applications attempting to draw columns, grids, or fill the display. Window and buffer size will match in a [pseudoconsole](pseudoconsole.md) session.

There are no plans to remove the Windows console APIs from the platform. On the contrary, the Windows console host has provided the [pseudoconsole](pseudoconsoles.md) technology to translate existing Windows command-line application calls into virtual terminal sequences and forward them to another hosting environment remotely or across platforms. This translation is not perfect and requires the console host window to maintain a simulated environment of what Windows would have displayed to the user and project a replica of that to the pseudoconsole host. All console API calls are operated within the simulated environment to serve the needs of the legacy command-line client application and only the effects are propagated onto the final host.

A command-line application desiring full compatibility across platforms and full support of all new features and scenarios both on Windows and elsewhere is therefore recommended to move to Virtual Terminal sequences and adjust the architecture of command-line applications to align with all platforms.

More information about this Windows transition for command-line applications can be found on our [ecosystem roadmap](ecosystem-roadmap.md).
