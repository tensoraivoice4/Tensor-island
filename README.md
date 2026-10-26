# SILENTREAPER Dynamic Notch

A Windows 11 prototype of a MacBook-style top-centred dynamic notch. It is an independent Windows app, not Apple's macOS implementation.

## Current prototype features

- Borderless, top-centred notch with compact and expanded states.
- Animated expansion and collapse.
- Dark translucent glass-inspired styling with layered highlights.
- Battery percentage and AC/charging status.
- CPU and physical RAM usage.
- Adaptive mode: hides when a foreground window occupies the full screen; returns when you leave full-screen mode.
- No administrator permissions required.

## Important status

This repository contains the source and a GitHub Actions workflow that builds a Windows x64 executable. A Windows `.exe` cannot be compiled in the Linux environment used to prepare this ZIP, so the ZIP does **not** pretend to contain a compiled executable. Push this repository to GitHub and run the **Build Windows app** workflow; download its `SILENTREAPER-DynamicNotch-win-x64` artifact, which contains the published app and a ZIP.

This is an initial prototype. The glass is a custom visual approximation, not Apple's proprietary Liquid Glass renderer. Music session controls, system-volume events, notification integration, settings, and more advanced real-time refraction are not implemented yet.

## Build locally on Windows

Install the .NET 8 SDK, then run PowerShell in this folder:

```powershell
dotnet publish .\SILENTREAPER.DynamicNotch.csproj -c Release -r win-x64 --self-contained true -p:PublishSingleFile=true -p:IncludeNativeLibrariesForSelfExtract=true -o .\publish
```

Run `.\publish\SILENTREAPER.DynamicNotch.exe`.

## Build with GitHub Actions

1. Create a GitHub repository and upload/push all files in this folder.
2. Open **Actions** and enable workflows if GitHub asks.
3. Select **Build Windows app** and click **Run workflow** (or push to `main`/`master`).
4. Download the artifact named `SILENTREAPER-DynamicNotch-win-x64`.
5. Extract the artifact ZIP and run the executable.

## Controls

- Single-click the notch to expand.
- Double-click the shell to toggle expansion.
- Use the collapse button (`⌃`) or click it to collapse.
- It hides over detected full-screen windows. Full-screen detection is heuristic and may vary by application.

## Safety / scope

The app does not modify the Windows boot process, partitions, BitLocker, or the Tensor project. Review source code before running any executable downloaded from a public repository.
