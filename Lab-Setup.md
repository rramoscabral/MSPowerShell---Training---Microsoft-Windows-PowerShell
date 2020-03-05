# Software list to run the labs 

<br>

| Software | Link |
| --- | --- |
| Microsoft .NET Framework 4.5.1 (Offline Installer) | https://www.microsoft.com/en-US/download/details.aspx?id=40779 |
| PowerShell Core (Windows, Linux, Mac) | https://github.com/PowerShell/PowerShell/releases |
| Visual Studio Code | https://code.visualstudio.com/ |
| Visual Studio Code PowerShell Extension | https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell |
| Visual Studio Code Remote WSL (Preview) Extension | https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl |
| Windows Management Framework 5.1 | https://www.microsoft.com/en-us/download/details.aspx?id=54616 |
| Windows Terminal (Preview) | https://www.microsoft.com/en-us/p/windows-terminal-preview/9n0dx20hk701?activetab=pivot:overviewtab |
| WMI Explorer | https://cdn-powershell.pressidium.com/wp-content/uploads/2013/03/wmiexplorer.zip | 


<br>

**Using Linux on Windows 10**

If you are going to use the Windows 10 operating system, it is recommended to enable Microsoft Windows Subsystem Linux and install a distribution of your choice (For Az-220 it is recommended Ubunto LTS)

  How-to Install:
  
  1. Before installing any Linux distros for WSL, you must ensure that the "Windows Subsystem for Linux" optional feature is enabled using Windows PowerShell:
  ```powershell
    Install-Module PowerShellGet -Force
    Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
  ```
  2. You can install Linux distros from the Microsoft Store app or you can download and manually install Linux distros by clicking these links:
      * [Ubuntu 18.04](https://aka.ms/wsl-ubuntu-1804)
      * [Ubuntu 18.04 ARM](https://aka.ms/wsl-ubuntu-1804-arm)
      * [Ubuntu 16.04](https://aka.ms/wsl-ubuntu-1604)
      * [Debian GNU/Linux](https://aka.ms/wsl-debian-gnulinux)
      * [Kali Linux](https://aka.ms/wsl-kali-linux-new)
      * [OpenSUSE Leap 42](https://aka.ms/wsl-opensuse-42)
      * [SUSE Linux Enterprise Server 12](https://aka.ms/wsl-sles-12)
     * [Fedora Remix for WSL](https://github.com/WhitewaterFoundry/WSLFedoraRemix/releases/)
