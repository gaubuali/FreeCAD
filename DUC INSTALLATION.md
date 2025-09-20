<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" style="height:64px;margin-right:32px"/>

# Complete Working Steps to Compile FreeCAD from Source on Windows

## Prerequisites

- Windows 10/11 with sufficient disk space (10+ GB)
- Internet connection for downloads


## Step 1: Install Visual Studio 2022 Community

1. Download Visual Studio 2022 Community from https://visualstudio.microsoft.com/downloads/
2. Run the installer
3. Select **"Desktop development with C++"** workload
4. Install (takes 15-30 minutes)

## Step 2: Download FreeCAD LibPack

1. Visit https://github.com/FreeCAD/FreeCAD-LibPack/releases
2. Download **LibPack-1.1.0 Version 3.1.1.3** (the .7z file)
3. Extract to a simple path like `E:\FreeCAD_Dev\LibPack-1.1.0-v3.1.1.3-Release`

## Step 3: Clone FreeCAD Source Code

1. Open PowerShell or Command Prompt
2. Navigate to your development folder:

```powershell
cd E:\FreeCAD_Dev
```

3. Clone the repository:

```powershell
git clone --recursive https://github.com/FreeCAD/FreeCAD.git
```


## Step 4: Configure with CMake

1. Navigate to the FreeCAD source directory:

```powershell
cd E:\FreeCAD_Dev\FreeCAD
```

2. Run CMake configuration (use direct paths, not variables):

```powershell
cmake -G "Visual Studio 17 2022" `
      -DFREECAD_LIBPACK_DIR="E:\FreeCAD_Dev\LibPack-1.1.0-v3.1.1.3-Release" `
      -DFREECAD_COPY_LIBPACK_BIN_TO_BUILD=ON `
      -S "E:\FreeCAD_Dev\FreeCAD" `
      -B "E:\FreeCAD_Dev\FreeCAD\build"
```


## Step 5: Build FreeCAD

Choose one of these methods:

**Option A: Command Line Build**

```powershell
cmake --build E:/FreeCAD_Dev/FreeCAD/build --config Release
```

**Option B: Visual Studio IDE Build**

1. Open `E:\FreeCAD_Dev\FreeCAD\build\FreeCAD.sln` in Visual Studio
2. Select **Release** configuration from dropdown
3. Build → Build Solution (or Ctrl+Shift+B)

## Step 6: Run FreeCAD

After successful build, find your compiled FreeCAD executable at:

```
E:\FreeCAD_Dev\FreeCAD\build\bin\Release\FreeCAD.exe
```


## Key Points

- Use **direct paths** in CMake commands, not PowerShell variables
- LibPack v3.x requires Visual Studio 2022 (MSVC 143)
- Build process takes 30-60 minutes depending on system
- Choose Release configuration for optimal performance
- The `--recursive` flag in git clone is essential for submodules

This process gives you a fully functional, self-compiled FreeCAD installation ready for use or further development.

