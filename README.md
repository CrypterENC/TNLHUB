# TNLHUB

[![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)](https://github.com/yourusername/TNLHUB/releases)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/platform-Windows-blue.svg)](https://github.com/yourusername/TNLHUB/releases)

A comprehensive real-time telemetry tracking system for Euro Truck Simulator 2 (ETS2) on TruckersMP servers. Features automatic ETS2 detection, system tray integration, and seamless plugin installation.

## ✨ Features

- **🚛 Real-time Telemetry**: Complete ETS2 telemetry data capture using official SCS Telemetry SDK
- **🔍 Automatic Detection**: Smart installer that automatically finds and configures ETS2 installations
- **📊 Rich Data Display**: Dark-themed UI showing truck info, job details, position, and performance metrics
- **🔌 Plugin Integration**: Native DLL plugin that loads automatically with ETS2
- **📱 System Tray**: Runs in background with easy access via tray icon
- **📝 Comprehensive Logging**: All data logged to user documents with detailed timestamps
- **🛠️ Cross-Architecture**: Supports both x64 and x86 ETS2 installations
- **📦 One-Click Install**: Professional installer handles everything automatically

## 📥 Installation

### Prerequisites

- Windows 10 or later (64-bit recommended)
- Euro Truck Simulator 2 (Steam version)
- Internet connection for installation

### Quick Install (Recommended)

1. Download `TNLHUB_Setup_1.0.0.exe` from [Releases](https://github.com/CrypterENC/TNLHUB/tags)
2. Run as administrator
3. The installer automatically:
   - Detects your ETS2 installation
   - Installs the telemetry plugin
   - Creates desktop and Start Menu shortcuts
   - Sets up logging directory

### Manual Installation

If auto-detection fails or you prefer manual setup:

1. **Extract the application** to your preferred location
2. **Install the plugin**: Copy `ETS2Telemetry.dll` to:
   ```
   C:\Program Files (x86)\Steam\steamapps\common\Euro Truck Simulator 2\bin\win_x64\plugins\
   ```
   (Use `win_x86` for 32-bit ETS2 installations)

## 🚀 Usage

### Starting TNLHUB

- Launch from desktop shortcut or Start Menu
- Application runs in system tray
- Right-click tray icon for quick access

### Tracking Data

The system captures comprehensive telemetry including:

- **Game Status**: Running state, engine status
- **Vehicle Info**: Brand, model, odometer, damage percentage
- **Performance**: Speed, RPM, fuel level, gear position
- **Job Details**: Cargo info, source/destination, income, delivery time
- **Position**: Real-time X/Y/Z coordinates
- **Timestamps**: Last update time for all data points

### Logs and Data

- **Location**: `%USERPROFILE%\Documents\TNLHUB\`
- **Contents**: All telemetry data with timestamps
- **Format**: Human-readable text logs

## 🏗️ Architecture

### ETS2TelemetryPlugin (Native DLL)

- **Location**: `ETS2TelemetryPlugin/` folder
- **Purpose**: SCS Telemetry SDK plugin loaded by ETS2
- **Communication**: Writes data to Windows shared memory (`ETS2TelemetryData`)

### GUI Application (C# WPF)

- **Location**: Root project with `Views/`, `Services/`, `Models/`
- **Purpose**: Real-time display and logging of telemetry data
- **Key Components**:
  - `Views/MainWindow.xaml` - Dark UI with live data
  - `Services/TelemetryService.cs` - Shared memory reader
  - `Services/LoggerService.cs` - File logging system
  - `Models/GameState.cs` - Data structures

## 🛠️ Development

### Requirements

- Visual Studio 2022 or later
- .NET 9.0 SDK
- CMake (for plugin building)
- Inno Setup (for installer creation)

### Building from Source

1. **Clone the repository**:

   ```bash
   git clone https://github.com/yourusername/TNLHUB.git
   cd TNLHUB
   ```

2. **Build the GUI application**:

   ```bash
   dotnet build -c Release
   ```

3. **Build the ETS2 plugin**:

   ```bash
   # Requires CMake and Visual Studio Build Tools
   cmake -S ETS2TelemetryPlugin -B ETS2TelemetryPlugin/build -A x64
   cmake --build ETS2TelemetryPlugin/build --config Release
   ```

4. **Build the installer** (optional):
   ```bash
   cd Inno_setup
   "C:\Program Files (x86)\Inno Setup 6\ISCC.exe" setup.iss
   ```

## 🔧 Troubleshooting

### ETS2 Not Detected

- Ensure ETS2 is installed via Steam
- Try running installer with Steam closed
- Check custom Steam library locations

### Plugin Not Loading

- Verify `ETS2Telemetry.dll` is in correct plugins folder
- Ensure plugin is built for correct architecture (x64)
- Check ETS2 `game.log.txt` for loading errors

### No Telemetry Data

- Confirm ETS2 is running and plugin loaded
- Start GUI after reaching ETS2 main menu
- Verify shared memory name matches

### Application Won't Start

- Check logs in `%USERPROFILE%\Documents\TNLHUB\logs\`
- Run as administrator
- Ensure .NET 9.0 runtime installed

## 📁 Project Structure

```
TNL_HUB/
├── App.xaml / App.xaml.cs          # WPF application entry
├── Views/
│   ├── MainWindow.xaml            # Main UI
│   └── MainWindow.xaml.cs         # UI logic
├── Models/
│   └── GameState.cs               # Data models
├── Services/
│   ├── TelemetryService.cs        # Shared memory reader
│   ├── ConfigService.cs           # Configuration
│   └── LoggerService.cs           # Logging system
├── ETS2TelemetryPlugin/           # Native plugin
│   ├── CMakeLists.txt
│   ├── src/plugin.cpp
│   └── scs_sdk/include/...
├── Inno_setup/                    # Installer
│   └── setup.iss
└── README.md
```

## 🤝 Contributing

We welcome contributions! Please:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Guidelines

- Follow C# coding standards
- Add tests for new features
- Update documentation
- Test on multiple Windows versions

## 📄 License

This project is licensed under the MIT License - see [LICENSE](LICENSE) file for details.

## 🙏 Credits

- **Developer**: iDOR
- **ETS2 Plugin**: Custom implementation using SCS Telemetry SDK
- **Installer**: Inno Setup
- **UI Framework**: WPF with Material Design

## ⚠️ Disclaimer

This software is not officially affiliated with or endorsed by SCS Software or Euro Truck Simulator 2. Use at your own risk.

## 📋 Changelog

### v1.0.0 (2024-12-XX)

- 🎉 Initial release
- 🚀 Automatic ETS2 detection and plugin installation
- 📱 System tray integration
- 📊 Real-time telemetry display
- 📝 Comprehensive error handling and logging
- 📦 Professional one-click installer

---

Made with ❤️ for the trucking community by [iDOR](https://github.com/yourusername)
