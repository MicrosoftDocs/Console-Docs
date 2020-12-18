---
title: Console Selection
description: An accessibility application needs information about the user's selection in the console.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- '_win32_console_selection'
- 'base.console_selection'
- 'consoles.console_selection'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 2f631e1b-d502-45b7-9c15-34c01e913738
---

# Console Selection

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

An accessibility application needs information about the user's selection in the console. To retrieve the current console selection, call the [`GetConsoleSelectionInfo`](getconsoleselectioninfo.md) function. The [`CONSOLE_SELECTION_INFO`](console-selection-info-str.md) structure contains information about the selection, such as the anchor, coordinates, and status.
