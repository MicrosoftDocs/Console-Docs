---
title: Console Functions
description: The following functions are used to access a console.
MS-HAID:
- '\_win32\_console\_functions'
- 'base.console\_functions'
- 'consoles.console\_functions'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 2a0e5dcc-be48-42ab-a05a-96f68d012a67
---

# Console Functions


The following functions are used to access a console.

| Function                                                                 | Description                                                                                                                                 |
|--------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| [**AddConsoleAlias**](addconsolealias.md)                               | Defines a console alias for the specified executable.                                                                                       |
| [**AllocConsole**](allocconsole.md)                                     | Allocates a new console for the calling process.                                                                                            |
| [**AttachConsole**](attachconsole.md)                                   | Attaches the calling process to the console of the specified process.                                                                       |
| [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md)           | Creates a console screen buffer.                                                                                                            |
| [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md)         | Sets the text and background color attributes for a specified number of character cells.                                                    |
| [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md)         | Writes a character to the console screen buffer a specified number of times.                                                                |
| [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md)               | Flushes the console input buffer.                                                                                                           |
| [**FreeConsole**](freeconsole.md)                                       | Detaches the calling process from its console.                                                                                              |
| [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md)             | Sends a specified signal to a console process group that shares the console associated with the calling process.                            |
| [**GetConsoleAlias**](getconsolealias.md)                               | Retrieves the specified alias for the specified executable.                                                                                 |
| [**GetConsoleAliases**](getconsolealiases.md)                           | Retrieves all defined console aliases for the specified executable.                                                                         |
| [**GetConsoleAliasesLength**](getconsolealiaseslength.md)               | Returns the size, in bytes, of the buffer needed to store all of the console aliases for the specified executable.                          |
| [**GetConsoleAliasExes**](getconsolealiasexes.md)                       | Retrieves the names of all executables with console aliases defined.                                                                        |
| [**GetConsoleAliasExesLength**](getconsolealiasexeslength.md)           | Returns the size, in bytes, of the buffer needed to store the names of all executables that have console aliases defined.                   |
| [**GetConsoleCP**](getconsolecp.md)                                     | Retrieves the input code page used by the console associated with the calling process.                                                      |
| [**GetConsoleCursorInfo**](getconsolecursorinfo.md)                     | Retrieves information about the size and visibility of the cursor for the specified console screen buffer.                                  |
| [**GetConsoleDisplayMode**](getconsoledisplaymode.md)                   | Retrieves the display mode of the current console.                                                                                          |
| [**GetConsoleFontSize**](getconsolefontsize.md)                         | Retrieves the size of the font used by the specified console screen buffer.                                                                 |
| [**GetConsoleHistoryInfo**](getconsolehistoryinfo.md)                   | Retrieves the history settings for the calling process's console.                                                                           |
| [**GetConsoleMode**](getconsolemode.md)                                 | Retrieves the current input mode of a console's input buffer or the current output mode of a console screen buffer.                         |
| [**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md)               | Retrieves the original title for the current console window.                                                                                |
| [**GetConsoleOutputCP**](getconsoleoutputcp.md)                         | Retrieves the output code page used by the console associated with the calling process.                                                     |
| [**GetConsoleProcessList**](getconsoleprocesslist.md)                   | Retrieves a list of the processes attached to the current console.                                                                          |
| [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)         | Retrieves information about the specified console screen buffer.                                                                            |
| [**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md)     | Retrieves extended information about the specified console screen buffer.                                                                   |
| [**GetConsoleSelectionInfo**](getconsoleselectioninfo.md)               | Retrieves information about the current console selection.                                                                                  |
| [**GetConsoleTitle**](getconsoletitle.md)                               | Retrieves the title for the current console window.                                                                                         |
| [**GetConsoleWindow**](getconsolewindow.md)                             | Retrieves the window handle used by the console associated with the calling process.                                                        |
| [**GetCurrentConsoleFont**](getcurrentconsolefont.md)                   | Retrieves information about the current console font.                                                                                       |
| [**GetCurrentConsoleFontEx**](getcurrentconsolefontex.md)               | Retrieves extended information about the current console font.                                                                              |
| [**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md)       | Retrieves the size of the largest possible console window.                                                                                  |
| [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md)   | Retrieves the number of unread input records in the console's input buffer.                                                                 |
| [**GetNumberOfConsoleMouseButtons**](getnumberofconsolemousebuttons.md) | Retrieves the number of buttons on the mouse used by the current console.                                                                   |
| [**GetStdHandle**](getstdhandle.md)                                     | Retrieves a handle for the standard input, standard output, or standard error device.                                                       |
| [**HandlerRoutine**](handlerroutine.md)                                 | An application-defined function used with the [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) function.                              |
| [**PeekConsoleInput**](peekconsoleinput.md)                             | Reads data from the specified console input buffer without removing it from the buffer.                                                     |
| [**ReadConsole**](readconsole.md)                                       | Reads character input from the console input buffer and removes it from the buffer.                                                         |
| [**ReadConsoleInput**](readconsoleinput.md)                             | Reads data from a console input buffer and removes it from the buffer.                                                                      |
| [**ReadConsoleOutput**](readconsoleoutput.md)                           | Reads character and color attribute data from a rectangular block of character cells in a console screen buffer.                            |
| [**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md)         | Copies a specified number of foreground and background color attributes from consecutive cells of a console screen buffer.                  |
| [**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md)         | Copies a number of characters from consecutive cells of a console screen buffer.                                                            |
| [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md)           | Moves a block of data in a screen buffer.                                                                                                   |
| [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md)     | Sets the specified screen buffer to be the currently displayed console screen buffer.                                                       |
| [**SetConsoleCP**](setconsolecp.md)                                     | Sets the input code page used by the console associated with the calling process.                                                           |
| [**SetConsoleCtrlHandler**](setconsolectrlhandler.md)                   | Adds or removes an application-defined [**HandlerRoutine**](handlerroutine.md) from the list of handler functions for the calling process. |
| [**SetConsoleCursorInfo**](setconsolecursorinfo.md)                     | Sets the size and visibility of the cursor for the specified console screen buffer.                                                         |
| [**SetConsoleCursorPosition**](setconsolecursorposition.md)             | Sets the cursor position in the specified console screen buffer.                                                                            |
| [**SetConsoleDisplayMode**](setconsoledisplaymode.md)                   | Sets the display mode of the specified console screen buffer.                                                                               |
| [**SetConsoleHistoryInfo**](setconsolehistoryinfo.md)                   | Sets the history settings for the calling process's console.                                                                                |
| [**SetConsoleMode**](setconsolemode.md)                                 | Sets the input mode of a console's input buffer or the output mode of a console screen buffer.                                              |
| [**SetConsoleOutputCP**](setconsoleoutputcp.md)                         | Sets the output code page used by the console associated with the calling process.                                                          |
| [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md)     | Sets extended information about the specified console screen buffer.                                                                        |
| [**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md)         | Changes the size of the specified console screen buffer.                                                                                    |
| [**SetConsoleTextAttribute**](setconsoletextattribute.md)               | Sets the foreground (text) and background color attributes of characters written to the console screen buffer.                              |
| [**SetConsoleTitle**](setconsoletitle.md)                               | Sets the title for the current console window.                                                                                              |
| [**SetConsoleWindowInfo**](setconsolewindowinfo.md)                     | Sets the current size and position of a console screen buffer's window.                                                                     |
| [**SetCurrentConsoleFontEx**](setcurrentconsolefontex.md)               | Sets extended information about the current console font.                                                                                   |
| [**SetStdHandle**](setstdhandle.md)                                     | Sets the handle for the standard input, standard output, or standard error device.                                                          |
| [**WriteConsole**](writeconsole.md)                                     | Writes a character string to a console screen buffer beginning at the current cursor location.                                              |
| [**WriteConsoleInput**](writeconsoleinput.md)                           | Writes data directly to the console input buffer.                                                                                           |
| [**WriteConsoleOutput**](writeconsoleoutput.md)                         | Writes character and color attribute data to a specified rectangular block of character cells in a console screen buffer.                   |
| [**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md)       | Copies a number of foreground and background color attributes to consecutive cells of a console screen buffer.                              |
| [**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)       | Copies a number of characters to consecutive cells of a console screen buffer.                                                              |

 

 

 




