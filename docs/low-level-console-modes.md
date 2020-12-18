---
title: Low-Level Console Modes
description: The types of input events reported in a console's input buffer depend on the console's mouse and window input modes.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- '_win32_low_level_console_modes'
- 'base.low_level_console_modes'
- 'consoles.low_level_console_modes'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 41bfdc51-27cb-4d5e-898c-507ffc8789b9
---

# Low-Level Console Modes

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

The types of input events reported in a console's input buffer depend on the console's mouse and window input modes. The console's processed input mode determines how the system handles the CTRL+C key combination. To set or retrieve the state of a console's input modes, an application can specify a console input buffer handle in a call to the [`SetConsoleMode`](setconsolemode.md) or [`GetConsoleMode`](getconsolemode.md) function. The following modes are used with console input handles.

| Mode | Description |
|-|-|
| `ENABLE_MOUSE_INPUT`     | Controls whether mouse events are reported in the input buffer. By default, mouse input is enabled and window input is disabled. Changing either of these modes affects only input that occurs after the mode is set; pending mouse or window events in the input buffer are not flushed. The mouse pointer is displayed regardless of the mouse mode.                                                |
| `ENABLE_WINDOW_INPUT`    | Controls whether buffer-resizing events are reported in the input buffer. By default, mouse input is enabled and window input is disabled. Changing either of these modes affects only input that occurs after the mode is set; pending mouse or window events in the input buffer are not flushed. The mouse pointer is displayed regardless of the mouse mode.                                      |
| `ENABLE_PROCESSED_INPUT` | Controls the processing of input for applications using the high-level console I/O functions. However, if processed input mode is enabled, the CTRL+C key combination is not reported in the console's input buffer. Instead, it is passed on to the appropriate control handler function. For more information about control handlers, see [Console Control Handlers](console-control-handlers.md). |

The output modes of a screen buffer do not affect the behavior of the low-level output functions.
