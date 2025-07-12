## Choose how to install .NET

There are different ways to install .NET, and some products might manage their own version of .NET. If you install .NET through software that manages its own version of .NET, it might not be enabled system-wide. Make sure you understand the 影響of installing .NET through other software.

If you're unsure which method you should choose after reviewing the lists in the following sections, you probably want to use the [.NET Installer](https://learn.microsoft.com/en-us/dotnet/core/install/windows?WT.mc_id=dotnet-35129-website#net-installer).

[](https://learn.microsoft.com/en-us/dotnet/core/install/windows?WT.mc_id=dotnet-35129-website#developers)

### Developers

- [Visual Studio](https://learn.microsoft.com/en-us/dotnet/core/install/windows?WT.mc_id=dotnet-35129-website#install-with-visual-studio)
    
    Use **Visual Studio** to install .NET when you want to develop .NET apps using Visual Studio. Visual Studio manages its own copy of .NET. This method installs the SDK, Runtime, and Visual Studio templates.
    
- [Visual Studio Code - C# Dev Kit](https://learn.microsoft.com/en-us/dotnet/core/install/windows?WT.mc_id=dotnet-35129-website#install-with-visual-studio-code)
    
    Install the **C# Dev Kit** extension for Visual Studio Code to develop .NET apps. The extension can use an SDK that's already installed or install one for you.
    

[](https://learn.microsoft.com/en-us/dotnet/core/install/windows?WT.mc_id=dotnet-35129-website#users-and-developers)

### Users and Developers

- [.NET Installer(Preferred by tested with my laptop)](https://learn.microsoft.com/en-us/dotnet/core/install/windows?WT.mc_id=dotnet-35129-website#net-installer)
    
    Install .NET with a Windows Installer package, which is an executable that you run. This method can install the SDK and Runtime. Installs are performed system-wide.
    
- [Windows Package Manager (WinGet)](https://learn.microsoft.com/en-us/dotnet/core/install/windows?WT.mc_id=dotnet-35129-website#install-with-windows-package-manager-winget)
    
    Use **WinGet** to install .NET when you want to manage .NET through the command line. This method can install the SDK and Runtime. Installs are performed system-wide.
    
- [PowerShell](https://learn.microsoft.com/en-us/dotnet/core/install/windows?WT.mc_id=dotnet-35129-website#install-with-powershell)
    
    A PowerShell script that can automate the install of the SDK or Runtime. You can choose which version of .NET to install.