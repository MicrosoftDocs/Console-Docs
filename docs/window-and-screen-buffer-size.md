---
title: Window and Screen Buffer Size
description: The size of a screen buffer is expressed in terms of a coordinate grid based on character cells.
author: miniksa
ms.author: miniksa


MS-HAID:
- '\_win32\_window\_and\_screen\_buffer\_size'
- 'base.window\_and\_screen\_buffer\_size'
- 'consoles.window\_and\_screen\_buffer\_size'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 55246039-31eb-41ca-ad8e-d314cb508644
---

# Window and Screen Buffer Size


The size of a screen buffer is expressed in terms of a coordinate grid based on character cells. The width is the number of character cells in each row, and the height is the number of rows. Associated with each screen buffer is a window that determines the size and location of the rectangular portion of the console screen buffer displayed in the console window. A screen buffer's window is defined by specifying the character-cell coordinates of the upper left and lower right cells of the window's rectangle.

A screen buffer can be any size, limited only by available memory. The dimensions of a screen buffer's window cannot exceed the corresponding dimensions of either the console screen buffer or the maximum window that can fit on the screen based on the current font size (controlled exclusively by the user).

The [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function returns the following information about a screen buffer and its window:

-   The current size of the console screen buffer
-   The current location of the window
-   The maximum size of the window given the current screen buffer size, the current font size, and the screen size

The [**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md) function returns the maximum size of a console's window based on the current font and screen sizes. This size differs from the maximum window size returned by [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) in that the console screen buffer size is ignored.

To change a screen buffer's size, use the [**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md) function. This function fails if either dimension of the specified size is less than the corresponding dimension of the console's window.

To change the size or location of a screen buffer's window, use the [**SetConsoleWindowInfo**](setconsolewindowinfo.md) function. This function fails if the specified window-corner coordinates exceed the limits of the console screen buffer or the screen. Changing the window size of the active screen buffer changes the size of the console window displayed on the screen.

A process can change its console's input mode to enable window input so that the process is able to receive input when the user changes the console screen buffer size. If an application enables window input, it can use [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) to retrieve window and screen buffer size at startup. This information can then be used to determine the way data is displayed in the window. If the user changes the console screen buffer size, the application can respond by changing the way data is displayed. For example, an application can adjust the way text wraps at the end of the line if the number of characters per row changes. If an application does not enable window input, it must either use the inherited window and screen buffer sizes, or set them to the desired size during startup and restore the inherited sizes at exit. For additional information about window input mode, see [Low-Level Console Modes](low-level-console-modes.md).

 

 




