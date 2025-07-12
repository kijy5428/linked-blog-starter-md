
https://learn.microsoft.com/en-us/dotnet/core/install/how-to-detect-installed-versions?pivots=os-windows


## Check for install folders

It's possible that .NET is installed but not added to the `PATH` variable for your operating system or user profile. In this case, the commands from the previous sections may not work. As an alternative, you can check that the .NET install folders exist.

When you install .NET from an installer or script, it's installed to a standard folder. Much of the time the installer or script you're using to install .NET gives you an option to install to a different folder. If you choose to install to a different folder, adjust the start of the folder path.

- **dotnet executable**  
    _C:\program files\dotnet\dotnet.exe_
    
- **.NET SDK**  
    _C:\program files\dotnet\sdk\{version}\_
    
- **.NET Runtime**  
    _C:\program files\dotnet\shared\{runtime-type}\{version}\_