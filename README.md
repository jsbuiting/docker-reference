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

   
# Jupyter notebook (for Data Science) via Docker

1. Pull the right image from [Jupyter - Docker Images](https://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html). In this case, the scipy-notebook from [Docker](https://hub.docker.com/r/jupyter/scipy-notebook)
   ```
   docker pull jupyter/scipy-notebook
   ```
1. Run the image with some options:
   * --name for a recognizable name (when stopped and started)
   * -p for mapping the ports
   * -v for mounting a local folder with the mounted folder
   ```
   docker run --name jnds -p <CHOOSE PORT>:8888 -v <LOCAL PATH e.g. C:\project\>:/home/jovyan/ jupyter/scipy-notebook:latest
   ```
1. If done, stop the image by getting the id of the container first.
   ```
   docker ps
   docker stop <CONTAINER ID>
   ```
1. Restart with
   ```
   docker container ls -a
   docker start <CONTAINER ID>
   ```
1. Remove, if neccesary, with
   ```
   docker container ls -a
   docker rm <CONTAINER ID>
   ```
