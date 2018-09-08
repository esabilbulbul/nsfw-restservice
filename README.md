# nsfw-webservice
NSFW (Not Suitable for Work) Web Service

Author: Software Engineer @ [shipshuk](http://www.shipshuk.com)

This repository explains running Yahoo's nsfw algorithm to run as a rest service. The service will be running on docker. The service fed with some 
dataset of 1000 pictures. The output of the rest service will be the rating between 0-1 about the picture if it is Not Suitable for Work content (adult/nudity content)

The Environment & Softwares used
- Docker
- Python3
- NSFW Yahoo's
- NGINX
- UWSGI
- Windows 10: I use windows 7 then upgraded to w10 later. I would recommend to run this on w10 as some of the things on w7 has some issues.

The deployment document is uploaded (ShipShuk_NudityAlgorithm_Deployment.pdf). Section 9 is "Deploying NSFW API" is the section should be walked 
thru for the implementation. 

#OVERVIEW

This deployment of NSFW described here explains nsfw implementation on windows 10. The docker image will running on ubuntu, the image files that will be checked located on windows side. This means we will be mounting drives to the container side. 
Deployment of NSFW algorithm completed in a couple steps. These are 

-	Preparation of base image
-	Preparation of final image
-	Running container

In first step, the base application such as ubuntu, python, web & app servers and so on are installed into the application. The second phase is to install some other packages requiring human interactivity. Just because we were not able to manage to run expect scripts / auto responding scripts for docker image buildings we chose to create this final step. The packages installed in this step will be committed to a new image which will be our final base image.
The final step will be running the docker with the volumes that will be used by the service. 
Before starting to deployment steps there are a few parameters that needs to be set correctly that will be used for integration from windows to ubuntu side.

#Once the implementation completed, you can test the service and the api as following

- to test the services up and running
http://127.0.0.1:9090/

- to test the image through nsfw api
http://127.0.0.1:9090/predict/test/08172018?f=lowneck1.jpg

