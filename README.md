# RemoteFileDialog

![Build](https://github.com/zameerthakur/RemoteFileDialog/actions/workflows/ci.yml/badge.svg)
![License](https://img.shields.io/github/license/zameerthakur/RemoteFileDialog)
![NuGet](https://img.shields.io/nuget/v/RemoteFileDialog.Wpf)
![Downloads](https://img.shields.io/nuget/dt/RemoteFileDialog.Wpf)

Reusable WPF dialogs for browsing and selecting files and folders from FTP and SFTP servers.

## Overview

RemoteFileDialog is a .NET WPF component that provides reusable dialog windows for remote file and folder selection.

It is designed for desktop applications that need FTP or SFTP browsing without building a custom remote explorer from scratch.

## Features

- FTP browsing support
- SFTP browsing support
- Remote folder selection dialog
- Remote file selection dialog
- Multi-file selection support
- TreeView folder navigation
- Connection monitoring
- Reconnect handling
- Loading indicators and status feedback
- Header checkbox for select all / deselect all files
- SFTP password authentication
- SFTP private key authentication
- SFTP password and private key authentication
- Human-readable file size formatting
- Standardized date formatting
- Professional vector-based icons
- Reusable MVVM-friendly architecture

## Packages

| Package | Description | NuGet |
|---|---|---|
| RemoteFileDialog.Wpf | Main WPF package containing remote folder and file selection dialogs. Recommended package for most applications. | https://www.nuget.org/packages/RemoteFileDialog.Wpf |
| RemoteFileDialog.Core | Shared models, enums, interfaces, and helper classes used by RemoteFileDialog. | https://www.nuget.org/packages/RemoteFileDialog.Core |
| RemoteFileDialog.Infrastructure | FTP and SFTP infrastructure implementation using FluentFTP and SSH.NET. | https://www.nuget.org/packages/RemoteFileDialog.Infrastructure |

### Main Package

Install the main package:

```powershell
dotnet add package RemoteFileDialog.Wpf
```

The following packages are installed automatically as dependencies:

- RemoteFileDialog.Core
- RemoteFileDialog.Infrastructure

## Supported Protocols

- FTP
- FTPS
- SFTP

## Target Framework

- .NET 8
- WPF
- Windows

## Quick Examples

### FTP Folder Dialog

```csharp
var connection = new RemoteConnectionOptions
{
    ConnectionType = RemoteConnectionType.Ftp,
    Host = "ftp.example.com",
    Port = 21,
    Username = "username",
    Password = "password"
};

var dialog = new RemoteFolderDialog(connection);

if (dialog.ShowDialog() == true)
{
    var selectedFolder = dialog.SelectedFolderPath;
}
```

### SFTP Folder Dialog (Password Authentication)

```csharp
var connection = new RemoteConnectionOptions
{
    ConnectionType = RemoteConnectionType.Sftp,
    Host = "sftp.example.com",
    Port = 22,
    Username = "username",
    Password = "password"
};

var dialog = new RemoteFolderDialog(connection);

if (dialog.ShowDialog() == true)
{
    var selectedFolder = dialog.SelectedFolderPath;
}
```

### SFTP Folder Dialog (Private Key Authentication)

```csharp
var connection = new RemoteConnectionOptions
{
    ConnectionType = RemoteConnectionType.Sftp,
    Host = "sftp.example.com",
    Port = 22,
    Username = "username",
    SftpAuthType = SftpAuthType.PrivateKey,
    PrivateKeyPath = @"C:\Keys\private-key.ppk",
    PrivateKeyPassphrase = "optional-passphrase"
};

var dialog = new RemoteFolderDialog(connection);

if (dialog.ShowDialog() == true)
{
    var selectedFolder = dialog.SelectedFolderPath;
}
```

### Remote File Dialog (Multi-Select)

```csharp
var connection = new RemoteConnectionOptions
{
    ConnectionType = RemoteConnectionType.Sftp,
    Host = "sftp.example.com",
    Port = 22,
    Username = "username",
    Password = "password"
};

var dialog = new RemoteFilePickerDialog(
    connection,
    new RemoteDialogOptions
    {
        AllowMultipleSelection = true
    });

if (dialog.ShowDialog() == true)
{
    var selectedFiles = dialog.SelectedFilePaths;
}
```

## Screenshots

### Remote Folder Dialog

![Remote Folder Dialog](assets/screenshots/folder-dialog.png)

### Remote File Dialog

![Remote File Dialog](assets/screenshots/file-dialog.png)

## Documentation

- [Getting Started](docs/getting-started.md)
- [Authentication](docs/authentication.md)
- [Folder Dialog](docs/folder-dialog.md)
- [File Dialog](docs/file-dialog.md)
- [Architecture](docs/architecture.md)
- [Troubleshooting](docs/troubleshooting.md)

## Project Structure

```text
RemoteFileDialog.Core
RemoteFileDialog.Infrastructure
RemoteFileDialog.Wpf
RemoteFileDialog.SampleApp
```

## 🚧 Project Status

This project is actively maintained, and the core FTP/SFTP browsing functionality is implemented and usable.

### ✅ Completed

- FTP browsing support
- SFTP browsing support
- Password authentication
- Private key authentication
- Password and private key authentication
- Remote folder selection dialog
- Remote file selection dialog
- Multi-file selection support
- Connection monitoring with automatic status updates
- Reconnect handling
- TreeView navigation with path synchronization
- Header checkbox for select all / deselect all files
- Loading indicators and UI status feedback
- Professional vector-based icons
- Standardized date formatting
- Human-readable file size formatting
- Documentation and usage examples
- Sample WPF application for testing
- NuGet package publishing

### 🔜 Planned

- Advanced filtering and sorting
- Dark mode support
- Search support
- File type filtering
- Localization support
- Keyboard navigation improvements
- Additional UI/UX polish
- TreeView lazy loading improvements

## Third-Party Libraries

This project uses the following open-source libraries:

- FluentFTP (MIT License)
- SSH.NET (MIT License)
- CommunityToolkit.Mvvm (MIT License)

## License

This project is licensed under the MIT License.
