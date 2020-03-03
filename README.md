# Install instructions Docker Desktop on Windows 10 - Enterprise

Quick instructions on how to install docker on Windows 10 Enterprise edition.

1. Download Docker Desktop from the [Docker page](https://docs.docker.com/docker-for-windows/install/).
1. Restart the computer and enter BIOS
1. Make sure virtualization is enabled, save BIOS and restart.
1. Go to Control panel -> Uninstall a program -> Turn Windows features on or off. Make sure Hyper-V is enabled.
1. Install (using administrator rights) and follow the wizard, but leave all boxes unchecked in the last window before clicking done.
1. Check if install went right
   ```console  
   $ docker --version
   $ docker run hello-world
   ```  


