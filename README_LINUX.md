# StarBreak Proton Enhancement (SBPE) - Linux Setup Guide

This guide will help you set up the StarBreak Proton Enhancement (SBPE) mod to work on Linux using Steam's Proton compatibility layer.

## Prerequisites

- Steam installed on your Linux system
- Proton compatibility layer (latest stable version recommended)

## Installation Steps

### 1. Download StarBreak

1. Open Steam
2. Search for and download **StarBreak** (Windows version)
3. Let the game download completely

### 2. Create Modded Directory Structure

1. Locate your StarBreak installation in Steam's `steamapps/common/` directory
2. Create a directory named **StarBreak_modded**
3. Copy the contents of the **StarBreak** folder into the **StarBreak_modded/StarBreak/** directory
4. Your directory structure should look like:
   ```
   ~/.local/share/Steam/steamapps/common/
   ├── StarBreak/
   └── StarBreak_modded/
       └── StarBreak/
   ```

### 3. Create Dummy Executable for Steam

1. Navigate to the `StarBreak_modded` directory
2. Create an empty file named `sbpe.exe`:
   ```bash
   touch ~/.local/share/Steam/steamapps/common/StarBreak_modded/sbpe.exe
   ```
   
   *Note: This file doesn't need any content - it's just to ease the installation of the folder in Steam as a non-Steam game.*

### 4. Add to Steam Library

1. In Steam, click **"Games"** → **"Add a Non-Steam Game to My Library..."**
2. Browse to and select the `sbpe.exe` file you just created
3. The game will now appear in your Steam library as "sbpe"

### 5. Configure Launch Options

1. Right-click on **StarBreak_modded** (or "sbpe") in your Steam library
2. Select **"Properties..."**
3. In the **"TARGET"** field, change the path to:
   ```
   /home/[insert_linux_username_here]/.local/share/Steam/steamapps/common/StarBreak_modded/run.bat
   ```
   
   *Replace `[insert_linux_username_here]` with your actual Linux username.*

4. Under **"COMPATIBILITY"**, check **"Force the use of a specific Steam Play compatibility tool"**
5. Select the **latest stable version of Proton** from the dropdown list

### 6. Configure SBPE

1. Copy `config_template.ini` to `config.ini`:
   ```bash
   cp config_template.ini config.ini
   ```

2. Edit the `config.ini` file and set the game path under the `[general]` section:
   ```ini
   [general]
   game = Z:\home\[insert_linux_username_here]\.local\share\Steam\steamapps\common\StarBreak_modded\StarBreak\mvmmoclient.exe
   ```
   
   *Replace `[insert_linux_username_here]` with your actual Linux username.*
   
   *Note: Proton maps Linux paths to Windows-style Z: drives, hence the Z:\ prefix.*

### 7. Launch and Play

1. Click **"Play"** on StarBreak_modded in your Steam library
2. Steam will launch the game through Proton with the SBPE enhancements
3. Enjoy the modded game in Steam using Proton on Linux!

## Troubleshooting

### Common Issues

- **Game doesn't launch**: Verify that your Proton version is up to date and that all paths in `config.ini` are correct
- **Missing dependencies**: Make sure you have all necessary 32-bit and 64-bit libraries installed for gaming on Linux
- **Performance issues**: Try adjusting Proton settings or using a different Proton version

### Path Examples

Replace `[insert_linux_username_here]` with your actual username:

**Example TARGET field:**
```
/home/john/.local/share/Steam/steamapps/common/StarBreak_modded/run.bat
```

**Example config.ini game path:**
```ini
game = Z:\home\john\.local\share\Steam\steamapps\common\StarBreak_modded\StarBreak\mvmmoclient.exe
```

## File Structure After Installation

```
~/.local/share/Steam/steamapps/common/
├── StarBreak/                    # Original Steam installation
└── StarBreak_modded/
    ├── StarBreak/                # Game files
    │   └── [game files...]
    ├── sbpe.exe                  # Dummy executable for Steam
    ├── run.bat                   # Main launcher script
    ├── config.ini                # SBPE configuration
    ├── config_template.ini       # Configuration template
    ├── [other SBPE files...]
```

## Notes

- This setup uses Proton's compatibility layer to run the Windows version of StarBreak on Linux
- The dummy `sbpe.exe` file is required for Steam to recognize the directory as a game
- All paths must use the full absolute path for reliable operation
- The `Z:\` prefix is required in `config.ini` because Proton maps Linux filesystems to Windows drive letters
