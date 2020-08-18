---
title: High-Level Console Modes
description: The behavior of the high-level console functions is affected by the console input and output modes.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- '\_win32\_high\_level\_console\_modes'
- 'base.high\_level\_console\_modes'
- 'consoles.high\_level\_console\_modes'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 3ec915eb-333d-484d-a14d-46377b503ecc
---

# High-Level Console Modes


The behavior of the high-level console functions is affected by the console input and output modes. All of the following console input modes are enabled for a console's input buffer when a console is created:

- Line input mode
- Processed input mode
- Echo input mode

Both of the following console output modes are enabled for a console screen buffer when it is created:

- Processed output mode
- Wrapping at EOL output mode

All three input modes, along with processed output mode, are designed to work together. It is best to either enable or disable all of these modes as a group. When all are enabled, the application is said to be in "cooked" mode, which means that most of the processing is handled for the application. When all are disabled, the application is in "raw" mode, which means that input is unfiltered and any processing is left to the application.

An application can use the [**GetConsoleMode**](getconsolemode.md) function to determine the current mode of a console's input buffer or screen buffer. You can enable or disable any of these modes by using the following values in the [**SetConsoleMode**](setconsolemode.md) function. Note that setting the output mode of one screen buffer does not affect the output mode of other screen buffers.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Mode</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>ENABLE_PROCESSED_INPUT</strong></td>
<td>Used with a console input handle to cause the system to process any system editing or control key input rather than returning it as input in the read operation&#39;s buffer. If line input is also enabled, backspaces and carriage returns are handled correctly. A backspace causes the cursor to move back one space without affecting the character at the cursor position. A carriage return is converted to carriage return – line feed character combination. If echo input mode is enabled and the output should reflect system editing, processed output must be enabled for the active screen buffer. If processed input is enabled, the CTRL+C key combination is passed on to the appropriate handler regardless of whether line input is enabled. For more information about control handlers, see <a href="console-control-handlers.md" data-raw-source="[Console Control Handlers](console-control-handlers.md)">Console Control Handlers</a>.</td>
</tr>
<tr class="even">
<td><strong>ENABLE_LINE_INPUT</strong></td>
<td>Used with a console input handle to cause the <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> and <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> functions to return when the ENTER key is pressed. If line input mode is disabled, the functions return when one or more characters are available in the input buffer.</td>
</tr>
<tr class="odd">
<td><strong>ENABLE_ECHO_INPUT</strong></td>
<td>Used with a console input handle to cause keyboard input read by the <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> function to be echoed to the active screen buffer. Characters are echoed only if the process that calls <strong>ReadFile</strong> or <strong>ReadConsole</strong> has an open handle to the active screen buffer. Echo mode cannot be enabled unless line input is also enabled. The output mode of the active screen buffer affects the way echoed input is displayed.</td>
</tr>
<tr class="even">
<td><strong>ENABLE_PROCESSED_OUTPUT</strong></td>
<td>Used with a console screen buffer handle to cause the system to perform the appropriate action for ANSI control characters that are written to a screen buffer. The backspace, tab, bell, carriage return, and line feed characters are processed. A tab character moves the cursor to the next tab stop, which occurs every eight characters. A bell character sounds a short tone.</td>
</tr>
<tr class="odd">
<td><strong>ENABLE_WRAP_AT_EOL_OUTPUT</strong></td>
<td>Used with a console screen buffer handle to cause the current output position (cursor position) to move to the first column in the next row (line) when the end of the current row is reached. If the bottom of the window region is reached, the window origin is moved down one row. This movement has the effect of scrolling the contents of the window up one row. If the bottom of the console screen buffer is reached, the contents of the console screen buffer are scrolled up one row, and the top row of the console screen buffer is discarded.
<p>If this mode is disabled, the last character in the row is overwritten with any subsequent characters.</p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

 

 




