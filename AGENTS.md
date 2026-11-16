# AGENTS.md — OSB XWin

This file guides coding agents working in the `osb.xwin` repository.

## Project Identity

**OSB XWin** is a text-mode graphical window manager for OSB (Operating System Basic), inspired by Windows 3.11. It is a freestanding NativeAOT ring-3 program that provides a desktop-like window manager environment on top of the OSB kernel.

## Code Policy

1. **Implementation Language**
   - Use **C#** for all XWin logic and rendering.
   - Use **assembly only where necessary** for lowest-level hardware access.

2. **Freestanding Constraints**
   - No BCL convenience, no GC allocations, no exceptions for normal control flow.
   - Fixed/stack buffers where appropriate.
   - Deterministic, bounded behavior over convenience frameworks.

3. **Dependencies**
   - Depends on `osb.toolkit` for GUI framework (windows, controls, graphics).
   - Depends on `osb.core` for shared runtime library (MiniCoreLib).
   - Communicates with OSB kernel via INT 21h syscalls.

## Architecture

The XWin system is organized into focused modules:

- **Program.cs** - Entry point
- **Desktop.cs** - Desktop environment management
- **Desktop.Input.cs** - Mouse/keyboard input handling
- **Desktop.Menu.cs** - Menu system
- **Desktop.Paint.cs** - Rendering and repaint logic
- **WindowManager.cs** - Window management
- **WindowManager.Capture.cs** - Screen capture
- **WindowManager.Paint.cs** - Window rendering
- **Arena.cs** - Memory arena management
- **Font.cs** - Font rendering
- **Gfx.cs** - Graphics primitives
- **Input.cs** - Input handling
- **Palette.cs** - Color palette management
- **Sys.cs** - System calls interface
- **MiniCoreLib.cs** - Minimal runtime stubs

## Build and Validation

```bash
./build.sh
```

Validation expectations:

- Build succeeds.
- Binary is produced (xwin.exe).
- Can be loaded by the OSB kernel.

## Change Workflow for Agents

1. Inspect relevant files first.
2. Keep edits targeted.
3. Do not break compatibility with osb.toolkit or the OSB kernel.
4. Check file lengths before finishing (no file may exceed 400 lines).

## Non-Goals and Cautions

- Do not convert XWin to a Unix-like windowing system.
- Do not introduce host-OS runtime dependencies.
- Do not break compatibility with the OSB kernel's INT 21h ABI.

## Documentation Anchors

- `README.md`: High-level project/user documentation.