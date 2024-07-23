---
title: Classic Console APIs versus Virtual Terminal Sequences
description: Describes the contrast between the classic Win32 console API surface and the concept of virtual terminal sequences, sometimes also known as escape sequences, to write command-line applications.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, terminal, virtual terminal, escape sequences, vt, vt100, console api
---

# Classic Console APIs versus Virtual Terminal Sequences

Our recommendation is to replace the classic **Windows Console API** with **virtual terminal sequences**. This article will outline the difference between the two and discuss the reasons for our recommendation.

## Definitions

The classic **[Windows Console API](console-functions.md)** surface is defined as the series of C language functional interfaces on `kernel32.dll` with "Console" in the name.

**[Virtual terminal sequences](console-virtual-terminal-sequences.md)** is defined as a language of commands that's embedded in the standard input and standard output streams. Virtual terminal sequences use non-printable escape characters for signaling commands interleaved with normal printable text.

## History

The **Windows Console** provides a broad API surface for client command-line applications to manipulate both the output display buffer and the user input buffer. However, other non-Windows platforms have never afforded this specific API-driven approach to their command-line environments, choosing instead to use virtual terminal sequences embedded within the standard input and standard output streams. *(For a time, Microsoft supported this behavior too in early editions of DOS and Windows through a driver called ANSI.SYS.)*

By contrast, **virtual terminal sequences** (in a variety of dialects) drive the command-line environment operations for  all other platforms. These sequences are rooted in an [ECMA Standard](https://ecma-international.org/publications-and-standards/standards/ecma-48) and series of extensions by many vendors tracing back to Digital Equipment Corporation and Tektronix terminals, through to more modern and common software terminals, like [xterm](https://invisible-island.net/xterm/). Many extensions exist within the virtual terminal sequence domain and some sequences are more widely supported than others, but it is safe to say that the world has standardized on this as the command language for command-line experiences with a well-known subset being supported by virtually every terminal and command-line client application.

## Cross-Platform Support

**Virtual terminal sequences** are natively supported across platforms, making terminal applications and command-line utilities easily portable between versions and variations of operating systems, with the exception of Windows.

By contrast, **Windows Console APIs** are only supported on Windows. An extensive adapter or translation library must be written between Windows and virtual terminal, or vice-versa, when attempting to port command-line utilities from one platform or another.

### Remote Access

**Virtual terminal sequences** hold a major advantage for remote access. They require no additional work to transport, or perform remote procedure calls, over what is required to set up a standard remote command-line connection. Simply connecting an outbound and an inbound transport channel (or a single bidirectional channel) over a pipe, socket, file, serial port, or any other device is sufficient to completely carry all information required for an application speaking these sequences to a remote host.

On the contrary, the **Windows Console APIs** have only been accessible on the local machine and all efforts to remote them would require building an entire remote calling and transport interface layer beyond just a simple channel.

### Separation of Concerns

Some **Windows Console APIs** provide low-level access to the input and output buffers or convenience functions for interactive command-lines. This might include aliases and command history programmed within the console subsystem and host environment, instead of within the command-line client application itself.

By contrast, **other platforms** make memory of the current state of the application and convenience functionality the responsibility of the command-line utility or shell itself.

The **Windows Console** way of handling this responsibility in the console host and API makes it quicker and easier to write a command-line application with these features, removing the responsibility of remembering drawing state or handling editing convenience features. However, this makes it nearly impossible to connect those activities remotely across platforms, versions, or scenarios due to variations in implementations and availability. This way of handling responsibility also makes the final interactive experience of these Windows command-line applications completely dependent on the console host's implementation, priorities, and release cycle.

For example, advanced line editing features, like syntax highlighting and complex selection, are only possible when a command-line application handles editing concerns itself. The console could never have enough context to fully understand these scenarios in a broad manner like the client application can.

By contrast, other platforms use **virtual terminal sequences** to handle these activities and virtual terminal communication itself through reusable client-side libraries, like [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) and [ncurses](https://invisible-island.net/ncurses/ncurses.html). The final terminal is only responsible for displaying information and receiving input through that bidirectional communication channel.

### Wrong-Way Verbs

With **Windows Console**, some actions can be performed in the opposite-to-natural direction on the input and output streams. This allows Windows command-line applications to avoid the concern of managing their own buffers. It also allows Windows command-line apps to perform advanced operations, like simulating/injecting input on behalf of a user, or reading back some of the history of what was written.

While this provides additional power to Windows applications operating in a specific user-context on a single machine, it also provides a vector to cross security and privilege-levels or domains when used in certain scenarios. Such scenarios include operating between contexts on the same machine, or across contexts to another machine or environment.

Other platforms, which use **virtual terminal sequences**, do not allow this activity. The intent of our recommendation to transition from classic Windows Console to virtual terminal sequences is to converge with this strategy for both interoperability and security reasons.

### Direct Window Access

**Windows Console API surface** provides the exact window handle to the hosting window. This allows a command-line utility to perform advanced window operations by reaching into the wide gamut of Win32 APIs permitted against a window handle. These Win32 APIs can manipulate the window state, frame, icon, or other properties about the window.

By contrast, on other platforms with **virtual terminal sequences**, there is a narrow set of commands that can be performed against the window. These commands can do things like changing the window size or displayed title, but they must be done in the same band and under the same control as the remainder of the stream.

As Windows has evolved, the security controls and restrictions on window handles have increased. Additionally, the nature and existence of an application-addressable window handle on any specific user interface element has evolved, especially with the increased support of device form factors and platforms. This makes direct window access to command-line applications fragile as the platform and experiences evolve.

### Unicode

UTF-8 is the accepted encoding for Unicode data across almost all modern platforms, as it strikes the right balance between portability, storage size and processing time. However, Windows historically chose UTF-16 as its primary encoding for Unicode data. Support for UTF-8 is increasing in Windows and use of these Unicode formats does not preclude the usage of other encodings.

The **Windows Console** platform has supported and will continue to support all existing code pages and encodings. Use UTF-16 for maximum compatibility across Windows versions and perform algorithmic translation with UTF-8 if necessary. Increased support of UTF-8 is in progress for the console system.

UTF-16 support in the console can be utilized with no additional configuration via the _W_ variant of all console APIs and is a more likely choice for applications already well versed in UTF-16 through communication with the `wchar_t` and _W_ variant of other Microsoft and Windows platform functions and products.

UTF-8 support in the console can be utilized via the _A_ variant of Console APIs against console handles after setting the codepage to `65001` or `CP_UTF8` with the [**SetConsoleOutputCP**](setconsoleoutputcp.md) and [**SetConsoleCP**](setconsolecp.md) methods, as appropriate. Setting the code pages in advance is only necessary if the machine has not chosen "Use Unicode UTF-8 for worldwide language support" in the settings for Non-Unicode applications in the Region section of the Control Panel.

>[!NOTE]
> As of now, UTF-8 is supported fully on the standard output stream with the [**WriteConsole**](writeconsole.md) and [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) methods. Support on the input stream varies depending on the input mode and will continue to improve over time. Notably the default **["cooked"](high-level-console-modes.md)** modes on input do not fully support UTF-8 yet. The current status of this work can be found at [**microsoft/terminal#7777**](https://github.com/microsoft/terminal/issues/7777) on GitHub. The workaround is to use the algorithmically-translatable UTF-16 for reading input through [**ReadConsoleW**](readconsole.md) or [**ReadConsoleInputW**](readconsoleinput.md) until the outstanding issues are resolved.

## Recommendations

For all new and ongoing development on Windows, **virtual terminal sequences are recommended** as the way of interacting with the terminal. This will converge Windows command-line client applications with the style of application programming on all other platforms.

### Exceptions for using Windows Console APIs

A **limited subset of Windows Console APIs is still necessary** to establish the initial environment. The Windows platform still differs from others in process, signal, device, and encoding handling:

- The standard handles to a process will still be controlled with **[GetStdHandle](getstdhandle.md)** and **[SetStdHandle](setstdhandle.md)**.

- Configuration of the console modes on a handle to opt in to Virtual Terminal Sequence support will be handled with **[GetConsoleMode](getconsolemode.md)** and **[SetConsoleMode](setconsolemode.md)**.

- Declaration of code page or UTF-8 support is conducted with [**SetConsoleOutputCP**](setconsoleoutputcp.md) and [**SetConsoleCP**](setconsolecp.md) methods.

- Some level of overall process management may be required with the [**AllocConsole**](allocconsole.md), [**AttachConsole**](attachconsole.md) and [**FreeConsole**](freeconsole.md) to join or leave a console device session.

- Signals and signal handling will continue to be conducted with [**SetConsoleCtrlHandler**](setconsolectrlhandler.md), [**HandlerRoutine**](handlerroutine.md), and [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md).

- Communication with the console device handles can be conducted with [**WriteConsole**](writeconsole.md) and [**ReadConsole**](readconsole.md). These may also be leveraged through programming language runtimes in the forms of:
        - C Runtime (CRT): [Stream I/O](/cpp/c-runtime-library/stream-i-o) like **printf**, **scanf**, **putc**, **getc**, or [other levels of I/O functions](/cpp/c-runtime-library/input-and-output).
        - C++ Standard Library (STL): [iostream](/cpp/standard-library/iostream) like **cout** and **cin**.
        - .NET Runtime: [System.Console](/dotnet/api/system.console) like **Console.WriteLine**.

- Applications that must be aware of window size changes will still need to use [**ReadConsoleInput**](readconsoleinput.md) to receive them interleaved with key events as **ReadConsole** alone will discard them.

- Finding the window size must still be performed with [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) for applications attempting to draw columns, grids, or fill the display. Window and buffer size will match in a [pseudoconsole](pseudoconsoles.md) session.

## Future planning and pseudoconsole

There are no plans to remove the Windows console APIs from the platform.

On the contrary, the Windows Console host has provided the **[pseudoconsole](pseudoconsoles.md)** technology to translate existing Windows command-line application calls into virtual terminal sequences and forward them to another hosting environment remotely or across platforms.

This translation is not perfect. It requires the console host window to maintain a simulated environment of what Windows would have displayed to the user. It then projects a replica of this simulated environment to the **pseudoconsole** host. All Windows Console API calls are operated within the simulated environment to serve the needs of the legacy command-line client application. Only the effects are propagated onto the final host.

A command-line application desiring full compatibility across platforms and full support of all new features and scenarios both on Windows and elsewhere is therefore recommended to move to virtual terminal sequences and adjust the architecture of command-line applications to align with all platforms.

More information about this Windows transition for command-line applications can be found on our [ecosystem roadmap](ecosystem-roadmap.md).
