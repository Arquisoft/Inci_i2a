# Inci_i2a (Incidence System by team I2A)

This is the final product of the Incidence System built by our team during the course, using the following modules:

## Modules
- [Loader](https://github.com/Arquisoft/Loader_i2a)
- [Agents](https://github.com/Arquisoft/Agents_i2a)
- [InciManager](https://github.com/Arquisoft/InciManager_i2a)
- [InciDashboard](https://github.com/Arquisoft/InciDashboard_i2a)


## Authors
- [Jesús Atorrasagasti García](https://github.com/jesusatgar)
- [Juan Aza Gutiérrez](https://github.com/juanaza)
- [Lorena Castillero Corriols](https://github.com/lorenacasti)
- [Marcos Chacón Cadenas](https://github.com/chacon11)
- [Alba Cotarelo Tuñón](https://github.com/albacotarelo)
- [Javier Díez García](https://github.com/javicodema)

## How to run the final application

### **First step: Running Loader module**
The Loader module is only needed in order to add agents to the system. So we just have to run it once (we can run it more times following the same steps to add more agents). We clone the repository from [this link](https://github.com/Arquisoft/Loader_i2a) and we can just ran the JAR that is already created with the command:
``` java -jar Loader_i2a-0.0.1-jar-with-dependencies.jar <xls file> <mongoDB host> <csv file> ```
Where the xls file is the file that specifies the agents that will be created, the mongoDB host will be the place where mongo will run (for example, a mLab host or simply localhost) and the csv file is the file where the kind codes are declared.

### **Second step: Build images of the modules**
To deploy the complete application, we need to have the Agents, InciManager and InciDashboard modules running. As we were taught, we will have a Docker image for each module. In our case we have already built the three images and they are stored in the Codefresh registry. To do that, the steps are:
- Create a Codefresh account
- Add the repositories and build each one selecting the Dockerfile that is in the repository (Pipelines>Workflow>Build>Repo's Dockerfile and then we go back and click on Build)
![cap1](https://i.imgur.com/UJqnj14.png) ![cap2](https://i.imgur.com/LFZL5zI.png)
- If the build succeeds (if you don't change anything in the repository, it should), we will have our images created and stored in the Codefresh registry. We could check the URI by clicking on the Images section of the page and then clicking on the image of the module we want.

### **Third step: Deploy the application online**
With the images stored in the Codefresh registry, we just have to go to the Docker Swarm > Compositions section of Codefresh and create a new composition to run all the modules. You can use the content of the docker-compose.yml file we already have at this repository (remember to change the URI of each image by the URI you have generated when the image is built).
After that, you can click on the Launch button (the one with the rocket image) and after a short period of time, your application will be running online (for a limited amount of hours, unless you have a premium account).

### **Fourth step: Using the application**
To find the URL of each module, since they work in different ports, the best option is to go to the Docker Swarm > Environments section and after clicking on the environment we have created by launching the application we click on the More information button and then we click on the Open App button of the module we want to use: 
![cap3](https://i.imgur.com/QRmBNgj.png)

## External services used
- [CloudKarafka](https://www.cloudkarafka.com/)
- [mLab](https://mlab.com/)
