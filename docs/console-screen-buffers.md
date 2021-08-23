---
title: Console Screen Buffers
description: A screen buffer is a two-dimensional array of character and color data for output in a console window. 
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- '\_win32\_console\_screen\_buffers'
- 'base.console\_screen\_buffers'
- 'consoles.console\_screen\_buffers'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: f94995fc-5f5f-4fcd-969d-7e10020634c2
ms.localizationpriority: high
---

# Console Screen Buffers

A *screen buffer* is a two-dimensional array of character and color data for output in a console window. A console can have multiple screen buffers. The *active screen buffer* is the one that is displayed on the screen.

The system creates a screen buffer whenever it creates a new console. To open a handle to a console's active screen buffer, specify the **CONOUT$** value in a call to the [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) function. A process can use the [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) function to create additional screen buffers for its console. A new screen buffer is not active until its handle is specified in a call to the [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) function. However, screen buffers can be accessed for reading and writing whether they are active or inactive.

Each screen buffer has its own two-dimensional array of character information records. The data for each character is stored in a [**CHAR\_INFO**](char-info-str.md) structure that specifies the Unicode or ANSI character and the foreground and background colors in which that character is displayed.

A number of properties associated with a screen buffer can be set independently for each screen buffer. This means that changing the active screen buffer can have a dramatic effect on the appearance of the console window. The properties associated with a screen buffer include:

- Screen buffer size, in character rows and columns.
- Text attributes (foreground and background colors for displaying text to be written by the [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) or [**WriteConsole**](writeconsole.md) function).
- Window size and location (the rectangular region of the console screen buffer that is displayed in the console window).
- Cursor position, appearance, and visibility.
- Output modes (**ENABLE\_PROCESSED\_OUTPUT** and **ENABLE\_WRAP\_AT\_EOL\_OUTPUT**). For more information about console output modes, see [High-Level Console Modes](high-level-console-modes.md).

When a screen buffer is created, it contains space characters in every position. Its cursor is visible and positioned at the buffer's origin (0,0), and the window is positioned with its upper left corner at the buffer's origin. The size of the console screen buffer, the window size, the text attributes, and the appearance of the cursor are determined by the user or by the system defaults. To retrieve the current values of the various properties associated with the console screen buffer, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md), [**GetConsoleCursorInfo**](getconsolecursorinfo.md), and [**GetConsoleMode**](getconsolemode.md) functions.

Applications that change any of the console screen buffer properties should either create their own screen buffer or save the state of the inherited screen buffer during startup and restore it at exit. This cooperative behavior is required to ensure that other applications sharing the same console session are not impacted by the changes.

> [!TIP]
> It is recommended to use the [**alternate buffer mode**](console-virtual-terminal-sequences.md#alternate-screen-buffer) going forward, if possible, instead of creating a second screen buffer for this purpose. **Alternate buffer mode** offers increased compatibility across remote devices and with other platforms. Please see our discussion on [**classic console APIs versus virtual terminal**](classic-vs-vt.md) for more information.

## Cursor Appearance and Position

A screen buffer's cursor can be visible or hidden. When it is visible, its appearance can vary, ranging from completely filling a character cell to appearing as a horizontal line at the bottom of the cell. To retrieve information about the appearance and visibility of the cursor, use the [**GetConsoleCursorInfo**](getconsolecursorinfo.md) function. This function reports whether the cursor is visible and describes the appearance of the cursor as the percentage of a character cell that it fills. To set the appearance and visibility of the cursor, use the [**SetConsoleCursorInfo**](setconsolecursorinfo.md) function.

Characters written by the [high-level console I/O functions](high-level-console-i-o.md) are written at the current cursor location, advancing the cursor to the next location. To determine the current cursor position in the coordinate system of a screen buffer, use [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md). You can use [**SetConsoleCursorPosition**](setconsolecursorposition.md) to set the cursor position and, thereby, control the placement of text that is written or echoed by the high-level I/O functions. If you move the cursor, text at the new cursor location is overwritten.

> [!NOTE]
> Using the low-level functions to find the cursor position is discouraged. It is recommended to use [virtual terminal sequences](console-virtual-terminal-sequences.md) to query this position if necessary for advanced layouts. More information about preferring virtual terminal sequences can be found in the **[classic functions versus virtual terminal](classic-vs-vt.md)** document.

The position, appearance, and visibility of the cursor are set independently for each screen buffer.

## Character Attributes

Character attributes can be divided into two classes: color and DBCS. The following attributes are defined in the `WinCon.h` header file.

| Attribute | Meaning |
|-|-|
| **FOREGROUND\_BLUE** | Text color contains blue. |
| **FOREGROUND\_GREEN** | Text color contains green. |
| **FOREGROUND\_RED** | Text color contains red. |
| **FOREGROUND\_INTENSITY** | Text color is intensified. |
| **BACKGROUND\_BLUE** | Background color contains blue. |
| **BACKGROUND\_GREEN** | Background color contains green. |
| **BACKGROUND\_RED** | Background color contains red. |
| **BACKGROUND\_INTENSITY** | Background color is intensified. |
| **COMMON\_LVB\_LEADING\_BYTE** | Leading byte. |
| **COMMON\_LVB\_TRAILING\_BYTE** | Trailing byte. |
| **COMMON\_LVB\_GRID\_HORIZONTAL** | Top horizontal. |
| **COMMON\_LVB\_GRID\_LVERTICAL** | Left vertical. |
| **COMMON\_LVB\_GRID\_RVERTICAL** | Right vertical. |
| **COMMON\_LVB\_REVERSE\_VIDEO** | Reverse foreground and background attributes. |
| **COMMON\_LVB\_UNDERSCORE** | Underscore. |

The foreground attributes specify the text color. The background attributes specify the color used to fill the cell's background. The other attributes are used with [DBCS](/windows/win32/intl/double-byte-character-sets).

An application can combine the foreground and background constants to achieve different colors. For example, the following combination results in bright cyan text on a blue background.

`FOREGROUND_BLUE | FOREGROUND_GREEN | FOREGROUND_INTENSITY | BACKGROUND_BLUE`

If no background constant is specified, the background is black, and if no foreground constant is specified, the text is black. For example, the following combination produces black text on a white background. Red, green, and blue are specified for the background which combines to a white background. No flag colors are specified for the foreground so it is black.

`BACKGROUND_BLUE | BACKGROUND_GREEN | BACKGROUND_RED`

Each screen buffer character cell stores the color attributes for the colors used in drawing the foreground (text) and background of that cell. An application can set the color data for each character cell individually, storing the data in the **Attributes** member of the [**CHAR\_INFO**](char-info-str.md) structure for each cell. The current text attributes of each screen buffer are used for characters subsequently written or echoed by the high-level functions.

An application can use [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) to determine the current text attributes of a screen buffer and the [**SetConsoleTextAttribute**](setconsoletextattribute.md) function to set the character attributes. Changing a screen buffer's attributes does not affect the display of characters previously written. These text attributes do not affect characters written by the low-level console I/O functions (such as the [**WriteConsoleOutput**](writeconsoleoutput.md) or [**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md) function), which either explicitly specify the attributes for each cell that is written or leave the attributes unchanged.

> [!NOTE]
> Using the low-level functions to manipulate default and specific text attributes is discouraged. It is recommended to use [virtual terminal sequences](console-virtual-terminal-sequences.md) to set text attributes. More information about preferring virtual terminal sequences can be found in the **[classic functions versus virtual terminal](classic-vs-vt.md)** document.

## Font Attributes

The [**GetCurrentConsoleFont**](getcurrentconsolefont.md) function retrieves information about the current console font. The information stored in the [**CONSOLE\_FONT\_INFO**](console-font-info-str.md) structure includes the width and height of each character in the font.

The [**GetConsoleFontSize**](getconsolefontsize.md) function retrieves the size of the font used by the specified console screen buffer.

> [!NOTE]
> Using functions to find and manipulate font information is discouraged. It is recommended to operate command-line applications in a font neutral manner to ensure cross-platform compatibility as well as compatibility with host environments that allow the user to customize the font. More information user preferences and host environments including terminals, please see the **[ecosystem roadmap](ecosystem-roadmap.md)**.