# OSB XWin

A text-mode graphical window manager for OSB (Operating System Basic), inspired by Windows 3.11.

## Overview

`osb.xwin` is a freestanding NativeAOT ring-3 program that provides a desktop-like window manager environment on top of the OSB kernel. It runs in text mode using ANSI escape sequences and supports mouse input via the SGR protocol.

## Features

- **Window Manager** - Create, move, resize, and manage windows
- **Desktop Environment** - Taskbar, icons, and menu system
- **Text-Mode Graphics** - Rendering using VGA text mode with cursor tricks
- **Mouse Support** - Full mouse input via SGR protocol
- **Haiku-Style UI** - Modern left-deskbar layout inspired by Haiku OS

## Architecture

The XWin system is built on top of:
- **osb.toolkit** - GUI framework (windows, controls, graphics)
- **osb.core** - Shared runtime library (MiniCoreLib)
- **OSB Kernel** - Provides INT 21h syscalls for I/O

## Building

```bash
./build.sh
```

This produces an `xwin.exe` binary that can be loaded by the OSB kernel.

## Part of OSB

This is part of the [OSB](https://github.com/osb-system) - Operating System Basic project, a DOS-like operating system built from scratch.

## License

MIT License - see [LICENSE](LICENSE) for details.