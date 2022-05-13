# Installation Guide for <ins>W</ins>indows <ins>S</ins>ubsystem for <ins>L</ins>inux <ins>2</ins>

## Table of content

- [WSL2 with GPU acceleration](#GPU)
- [WSL2 with CPU only](#CPU)
- [More information](#info) (known issues, helpful tools, etc.)


  
## WSL2 with GPU acceleration <a id="GPU">
  
  This section mainly focuses on installing WSL2 with GPU acceleration. If you only need CPU access, please start from [here](#CPU). 
  
  ## 1. Check your Windows version
  
  Windows 11 or Windows 10, version 21H2 is needed to enable GPU acceleration. If you are using Windows 10 version 21H2, you might need to be in the **dev channel**. I personally tested with Windows 11 and can confirm that it is not need for Windows 11. If you don't have access to any required system, you could try installing WSL2 with CPU only instead.
  
  To check your Windows version: 
  
  - Windows 11: Windows -> Settings -> System -> About
  - Windows 10: Windows -> Settings -> About
  
  To upgrade your system, there are a few options:
  
  - Windows -> Settings -> Search for Windows Update -> Look for upgrade options.
  - Directly download and install Windows 11/10 by [Windows 11 installer](https://www.microsoft.com/software-download/windows11)/[Windows 10 installer](https://www.microsoft.com/en-us/software-download/windows10).
  - To try out Dev channel, please consult this website [Windows insider program](https://docs.microsoft.com/en-us/windows-insider/get-started).
  
  ## 2. Install/Update the NVIDIA driver
  
  Please [download and install the appropriate NVIDIA driver](https://www.nvidia.com/download/index.aspx) on your **Windows** system. In earlier times, there's a seperate driver for WSL but recently NVIDIA merged it into the currently available drivers. I personally installed the Game Ready Driver(GRD), but I suppose the Studio Drivers also have it. 
  
  Note that we will **not** need to install any drivers in the Linux system.
  
  ## 3. Install WSL2
  
  If WSL2 is not installed at all, please the following command in your Windows terminal/powershell. This command will download and set up WSL2 with Ubuntu by default
  ```
  wsl --install
  ```
  If you want some other Linux distribution, you can run the following 
  ```
  wsl.exe --install -d <Distribution Name>
  ```
  After the above is done, please go to Windows and search for the distribution that you installed. Take Ubuntu for example, we search for "Ubuntu for Windows". Open it and you should see a line of words saying
  

  > Installing, this may take a few minutes ...
  
  Giving some time to install, it should be ready to go in a few minutes. However, you might see something like
  
  > The virtual machine could not be started because a required feature is not installed
  
  In this case, there are a few things can be done:
  - Enable Virtual Machine Platform, Windows Subsystem for Linux, Windows Hypervisor Platform: <br>Windows -> Search for Turn Windows features on or off -> Look for these features
  - Enable Hardware/CPU virtualization:<br>Restart the machine -> go into BIOS mode -> enable virtualization (may have different names depending on you device)
  
  ## 4. Install softwares
  
  Now you can install your favorite softwares as how you would usually do! The last section contains some useful information for installing some softwares like Miniconda, CUDA, etc. 
  
  To verify that we do have GPU access, we can simply install Pytorch with CUDA and run
  ```
  import torch
  torch.cuda.is_available()
  torch.cuda.get_device_name(0)
  ```
  
  ##### Links
  - Official guide: https://docs.microsoft.com/en-us/windows/wsl/install 
  - Official trouble shooting: https://docs.microsoft.com/en-us/windows/wsl/troubleshooting#installation-issues 
  
  

## WSL2 with CPU only <a id="CPU">
  
  ##### Prerequisite
  - The host system should be running Windows 10 version 2004 and higher (Build 19041 and higher) or Windows 11. 

## More information <a id="info">
