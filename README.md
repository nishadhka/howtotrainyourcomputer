# How to train your computer?

SCCS-Bng 2018, long workshop for beginners

![alt text](https://raw.githubusercontent.com/nishadhka/howtotrainyourcomputer/master/flayer_httyc.png)

By all means today's personal computers are most powerful computing tool ever made. 
This workshop tries to show a set of exercises to train that dragon!. To get 
assistance from it in scientific work which are computationally and data intensive 
such as in the field of Conservation sciences. 

The scheme of training exercises proposed is as follows

**"Practice Galileo's annotation with a life boat all along having time travel!"**

Time travel-Version controlling system is computer's time machine.   

Life boat- Operating system virtualization/containerization- Docker

Galileo's annotation- Jupyter notebook

Python programming language is an easy to read and learn computing language. 
Its open source nature and wide usage gives rise to strong base of libraries 
and tools to address any complex and data intensive real world problems. 
Open source python distribution such as Anaconda simplifies creation of working environment. 
Tools like Jupyter notebook enhance the work flow which is intuitive, easy to share and 
collectively learn faster on data analysis using Python. This workshop intent to give 
introduction to these advantages of Python along with operating system virtualization and 
version controlling system for programming. It takes demonstration and do it yourself tasks 
on geospatial data, the workshop hopes to generate interest and show learning pathway for 
student to comfortable with Python programming language.

The workshop is comprised of three components, in which first component introduce the concept 
of operating system virtualization, version controlling and literal programming with Python environment 
and work flow setup. Second component discuss about the Python's applications in Vector data analysis 
and visualisation, third component on raster data with discussion on using Application Programming 
interface (APIs) for data sources such as of Google earth engine.

# To setup the working environment for the workshop

1. Laptop 32bit/64 bit
1. Workshop material is tested on 64 bit computer, it is said to be working in 32 bit, lets experiment!
1. A copy of Docker container image from [here](https://drive.google.com/file/d/1RbnQAiRJY40xO6ty2TPXxM5-4vqG1cl_), file from the link foss-pt-gsa_v3.tar.gz is 2.5 GB in size, will be using this container for DIY

**Linux**

1. Install docker, I followed [digital ocean install tutorial ](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-18-04),  which worked!.
1. Use docker to load downloaded tar into it as an container image, before that unzip the foss-pt-gsa_v3.tar.gz into foss-pt-gsa_v3.tar
```   
docker load -i  foss-pt-gsa_v3.tar 
```
1. To check the docker is loaded with new image, ensure the image ```foss-pt-gsa/foss-pt-gsa:version3``` is listed by entering
```
docker images
```
1. To run the image, enter
```
docker run -dit foss-pt-gsa/foss-pt-gsa:version3
```
1. Get the CONTAINER_ID of the just started container by the command ```docker ps```
1. To enter into the image bash
```
docker exec -it CONTAINER_ID bash
```
1. After enter into the image’s bash terminal, enter following commands. the commands download the workshop github repo zip file into a working direcoty, then unzip it and get into the repo folder to start a jupter notebook server 

        cd /home/ubuntu/  
        wget https://github.com/nishadhka/FOSS-Python-GeospatialAnalysis/archive/master.zip
        unzip master.zip
        cd FOSS-Python-GeospatialAnalysis-master
       jupyter notebook --ip=0.0.0.0 --port=8080 --allow-root
      
1. Note down the link provided by the jupyter notebook such as example http://0.0.0.0:8080/?token=c8e944b8397b0bde97b4d9284e5e3ffc0136658fcca3ea1e
1. Logout from the docker image bash (by typing ctrl+q or closing the bash window) and in the host computer note down the image_ID of the workshop image running inside the docker by
```
docker ps
```
1. Then inspect about the docker image to get to know the image’s IP address. Note down the ipaddress
```
docker inspect image_ID | grep "IPAddress"
```
1. Edit the jupter server given link as into http://ipaddress:8889/?token=c8e944b8397b0bde97b4d9284e5e3ffc0136658fcca3ea1e
1. Open the link in host computer browser, it shows the Jupyternotebooks in the workshop repo and click on the file docker_test.ipynb, to run the notebook and execute its first cell to ensure all the libraries for the workshop is working properly

**Windows**

1. Local copy of Docker toolbox from [here](https://docs.docker.com/toolbox/toolbox_install_windows/) for windows 64 bit, for 32 bit Windows, follow this [link](https://medium.com/@chrispatten/installing-and-running-docker-on-32-bit-windows-d18b95ee1fc3).
1. Local copy boot2docker.iso from [here](http://boot2docker.io/), it is better to follow old method of docker toolbox instead of docker native software for Windows.
1. save the iso file in C:\Users\User\.docker\machine\cache\boot2docker.iso
2. Open the program Docker quick start, It will make a separate virtual machine to run the docker container
3. Under the Docker quick start program, after the virtual machine run, check docker is working by entering command ```docker ps```
4. Now, import the workshop container by
	```
	docker load -i foss-pt-gsa_v3.tar
	```
5. Then run the imported container image by 
	```
	docker run --name jupyter1 --rm -it --user root -d -p 8080:8080 jupyter/r-notebook:version3
	```
6. again check the command ```docker ps```, it would show the container is running by having a container ID
7. To get into the running docker
	```
	docker exec -it container_ID bash
	```
1. After enter into the image’s bash terminal, enter following commands. the commands download the workshop github repo zip file into a working direcoty, then unzip it and get into the repo folder to start a jupter notebook server 

        cd /home/ubuntu/  
        wget https://github.com/nishadhka/FOSS-Python-GeospatialAnalysis/archive/master.zip
        unzip master.zip
        cd FOSS-Python-GeospatialAnalysis-master
        jupyter notebook --ip=0.0.0.0 --port=8080 --allow-root
      
1. Note down the link provided by the jupyter notebook such as example http://0.0.0.0:8080/?token=c8e944b8397b0bde97b4d9284e5e3ffc0136658fcca3ea1e
1. Replace the 0.0.0.0 with default 192.168.99.100 address of docker toolbox as per [this](https://stackoverflow.com/questions/42866013/docker-toolbox-localhost-not-working)

 
