# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

cool-retro-term is a Qt5/QML-based terminal emulator that mimics old CRT screens. This is a fork focused on providing Apple Silicon (arm64) Mac binaries through GitHub Actions, as the upstream project hasn't been updated in years.

## Build Commands

### Prerequisites
```bash
# Initialize git submodules (required)
git submodule update --init --recursive

# macOS: Install Qt5
brew install qt@5
brew link qt@5 --force
```

### Building
```bash
# Build for release
qmake -config release
make -j$(nproc)  # Linux
make -j$(sysctl -n hw.logicalcpu)  # macOS
```

### macOS Packaging
```bash
# Create app bundle with dependencies
mkdir cool-retro-term.app/Contents/PlugIns
cp -r qmltermwidget/QMLTermWidget cool-retro-term.app/Contents/PlugIns
macdeployqt cool-retro-term.app -qmldir=app/qml -dmg
```

## Architecture

### Core Structure
- **C++ Backend** (`app/`): System integration, font management, file I/O
- **QML Frontend** (`app/qml/`): UI, terminal container, shader effects
- **qmltermwidget** (git submodule): Terminal widget implementation

### Key Files
- `cool-retro-term.pro`: Main project file (subdirs: qmltermwidget, app)
- `app/app.pro`: Application build configuration
- `app/main.cpp`: Application entry point with Qt initialization
- `app/qml/main.qml`: Main application window
- `app/qml/ShaderTerminal.qml`: GPU-accelerated retro effects
- `app/qml/TerminalContainer.qml`: Terminal widget integration

### Dependencies
- Qt5 modules: qml, quick, widgets, sql, quickcontrols2
- qmltermwidget submodule (branch: unstable)

### Build System Notes
- Uses qmake (.pro files), not CMake or modern build systems
- Requires `CONFIG += ordered` to build qmltermwidget before app
- Resources (fonts, images, QML) embedded via `app/qml/resources.qrc`
- Cross-platform packaging supported (macOS dmg, deb, rpm, snap)

## Development Notes

This fork's primary purpose is maintaining Apple Silicon compatibility and automated builds. The upstream codebase is feature-complete, so changes should focus on:
- Build system maintenance
- Platform compatibility fixes
- CI/CD improvements

The qmltermwidget submodule handles all terminal functionality - UI and effects work is in the main app.