# Install instructions Docker Desktop on Windows 10 - Enterprise / Pro

Quick instructions on how to install docker on Windows 10 Enterprise / Pro edition.


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

See also:
* [Docker - Get Started](https://docs.docker.com/get-started/)
* [Intro to Docker](https://docker-curriculum.com/)


# Jupyter lab via Docker Desktop

1. Create a file named Dockerfile and place below inside. 

   ```
   FROM continuumio/anaconda3
   EXPOSE 8888
   CMD ["jupyter", "lab", "--ip='0.0.0.0'", "--port=8888", "--no-browser", "--allow-root"]
   ```
1. In the directory of the just made file execute following:
   ```
   docker build -t jupyterlab:1.0 ./
   ```
1. Run to start docker:
   ```
   docker run -p <PORT USED IN URL>:8888 -v C:\<DIR OF CHOICE>:/home/notebooks jupyterlab:1.0
   ```