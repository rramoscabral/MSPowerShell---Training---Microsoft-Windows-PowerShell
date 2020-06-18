# Software list to run the labs 

<br>

| Software | Link |
| --- | --- |
| Microsoft .NET Framework 4.5.1 (Offline Installer) | https://www.microsoft.com/en-US/download/details.aspx?id=40779 |
| PowerShell Core (Windows, Linux, Mac) | https://github.com/PowerShell/PowerShell/releases |
| Visual Studio Code | https://code.visualstudio.com/ |
| Visual Studio Code PowerShell Extension | https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell |
| Visual Studio Code Remote WSL Extension | https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl |
| Windows Management Framework 5.1 | https://www.microsoft.com/en-us/download/details.aspx?id=54616 |
| Windows Terminal | https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701/9n0dx20hk701?activetab=pivot:overviewtab |
| WMI Explorer | https://cdn-powershell.pressidium.com/wp-content/uploads/2013/03/wmiexplorer.zip | 


<br>

### Windows Subsystem for Linux (WSL)
----------
**Using Linux on Windows 10 or Windows Server 2019**

If you are going to use the Windows 10 operating system, it is recommended to enable Microsoft Windows Subsystem Linux and install a distribution of your choice

Windows 10
 * WSL 1 is only available in Windows 10 version 1607 (Anniversary Update) or higher
 * WSL 2 is only available in Windows 10 version 2004, Build 19041 or higher
    * [Comparing WSL 2 and WSL 1](https://docs.microsoft.com/en-us/windows/wsl/compare-versions)

Windows Server 2019
  * WSL 1 is only available in Windows Server 2019 version 1709 or higher
  * WSL 2 is only available in Windows Server Insider Preview build 18945 or higher

<br/>

How-to Install:
  
  1. Before installing any Linux distros for WSL, you must ensure that the "Windows Subsystem for Linux" optional feature is enabled using Windows PowerShell:
  ```powershell
    Install-Module PowerShellGet -Force
    Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux 
  ```
  This action requires restart
 
 <br/>
 
  2. You can install Linux distros from the Microsoft Store app or you can download and manually install Linux distros by clicking these links:
  

| Distrubtion| Microsof Store | Manually install |
| --- | --- | --- |
| Alpine WSL | [Microsoft Store](https://www.microsoft.com/store/apps/9p804crf0395) | Link not available | 
| Debian GNU/Linux | [Microsoft Store](https://www.microsoft.com/store/apps/9MSVKQC78PK6) | [Download](https://aka.ms/wsl-debian-gnulinux) | 
| Fedora Remix for WSL | [Microsoft Store](https://www.microsoft.com/store/apps/9n6gdm4k2hnc) | [Download](https://github.com/WhitewaterFoundry/WSLFedoraRemix/releases/) | 
| Kali Linux | [Microsoft Store](https://www.microsoft.com/store/apps/9PKR34TNCV07) | [Download](https://aka.ms/wsl-kali-linux-new) | 
| OpenSUSE Leap 42   | Link not available | [Download](https://aka.ms/wsl-opensuse-42) |
| OpenSUSE Leap 15.1 | [Microsoft Store](https://aka.ms/wsl2kernel)| Link not available | 
| Pengwin | [Microsoft Store](https://www.microsoft.com/store/apps/9NV1GV1PXZ6P) | Link not available | 
| Pengwin Enterprise | [Microsoft Store](https://www.microsoft.com/store/apps/9N8LP0X93VCP) | Link not available | 
| SUSE Linux Enterprise Server 12 | [Microsoft Store](https://www.microsoft.com/store/apps/9MZ3D1TRP8T1) | [Download](https://aka.ms/wsl-sles-12)  | 
| SUSE Linux Enterprise Server 15 | [Microsoft Store](https://www.microsoft.com/store/apps/9PN498VPMF3Z) | Link not available | 
| Ubuntu 16.04 | [Microsoft Store](https://www.microsoft.com/store/apps/9pjn388hp8c9) | [Download](https://aka.ms/wsl-ubuntu-1604) | 
| Ubuntu 18.04 | [Microsoft Store](https://www.microsoft.com/store/apps/9N9TNGVNDL3Q) | [Download](https://aka.ms/wsl-ubuntu-1804) | 
| Ubuntu 18.04 ARM | Link not available | [Download](https://aka.ms/wsl-ubuntu-1804-arm) |
| Ubuntu 20.04 | [Microsoft Store](https://www.microsoft.com/store/apps/9n6svws3rx71) | [Download](https://aka.ms/wslubuntu2004) | 
| Ubuntu 20.04 ARM | Link not available | [Download](https://aka.ms/wslubuntu2004arm) |
      
     
   **Warning about Ubunto 20.04:** Ubuntu 20.04 is an LTS release. PowerShell does not currently support this version. Support for this version is being considered for the PowerShell 7.1 release. Please upvote this [request](https://github.com/PowerShell/PowerShell/issues/12626) if you would like support for Ubuntu 20.04.
   

<br/>
       
  3. Set your distribution version to WSL 1 or WSL 2
  ```powershell
    # View Linux distribution
    
    wsl --list --verbose
    
    # To set a distribution
    wsl --set-version <distribution name> <versionNumber>
    
    # Make WSL 2 your default architecture
    wsl --set-default-version 2
  ```
<br/>
 
  4. You need to initialize the distro instance by running the command 'wsl'. It  will be prompted to create a new user account and password.
  
<br/>

  5. Is recomended that you update the distribution:
       * Debian/Kali/Ubunto: sudo apt update
       * Fedora: sudo dnf update
       * SUSE: sudo zypper update
    
 <br/> 
  
  6. For more information about WSL you can check the documentation [here](https://docs.microsoft.com/en-us/windows/wsl/about?redirectedfrom=MSDN) and the MSDN blog post about WSL [here](https://blogs.msdn.microsoft.com/commandline/learn-about-windows-console-and-windows-subsystem-for-linux-wsl/#primary).
