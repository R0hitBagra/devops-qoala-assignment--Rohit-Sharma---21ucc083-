# DevOps Assignment: Report

This project involves setting up and running an Nginx web server as a reverse proxy for a Flask application within Docker containers. Here is a summary of issues encountered, steps taken to resolve them, and the corrected code.

## Issues and Resolutions

### 1. Docker Installation Issue
**Issue:**
   - During the initial setup, I faced an issue while installing Docker. I was receiving proxy errors because Docker requires a Linux backend to operate, which in this case is WSL2 (Windows Subsystem for Linux).
   
**Resolution:**
   - Installed WSL2 using the command wsl --install, which set up Ubuntu as the Linux backend.
   - However, I continued to face issues because Docker was automatically selecting a proxy server that was blocking the image build process. I disabled the automatic proxy selection and switched to a manual proxy configuration.


### 2.  Nginx HTML Folder Not Found
**Issue:**
   - An error occurred when the Docker build could not locate the html folder in the Nginx container (/usr/share/nginx/html). This issue was due to a missing html folder in my project structure.
   
**Resolution:**
   - To resolve this, I created an html folder within the Nginx directory and added an index.html file to it. After making this adjustment, I rebuilt the Docker image, and Nginx could now access the html directory without issues.

### 3. Tagging Images for Docker Compose
**Issue:**
   - Initially, I encountered issues with Docker Compose failing to recognize the images because they weren't tagged correctly.
   
**Resolution:**
   - I tagged each Docker image explicitly (local-nginx:latest and local-python-app:latest) and updated the docker-compose.yml file to reference these tags. This allowed Docker Compose to locate and run the correct images.

### 4. Configuration and Typo Errors in Docker Files
**Error in nginx.conf:**
   - Fixed typos  mime.typess -> mime.types and default_typ -> default_type.
   
** Error in Dockerfile (nginx Dockerfile):**
   - Fixed errors "eighty" -> "80" and in line 3 COPY ./html /usr/share/nginx/html, the html folder did not exist in the specified location, causing a build error so I created the missing html folder with an index.html file.

** Error in Dockerfile (Python Dockerfile):**
   - Fixed the typo in COPY appy.py /app to COPY app.py /app, corrected the spelling of package netiface to netifaces. Changed EXPOSE "eight thousand" to EXPOSE 8000. Fixed "pythn" in CMD to "python".

**Error in docker-compose.yaml:**
   - Changed eighty:80 to "80:80" in ports for the nginx service to ensure correct port mapping, corrected nginx.confi to nginx.conf in volumes for the nginx service, replaced "eight thousand" with "8000" in expose for the python-app service, corrected bridg to bridge in networks for nginx-network, removed the invalid options field (compelex_option: value) under networks as it was not a valid property and causing an error.
   
---

## Screenshots

   ### 1. Application running in the browser

   ### 2. Nginx Access Logs



### Cloud Deployment
   -


Best Regards,
Rohit Sharma
21ucc083
