# Simple Dockerfiles for applications

# Creating the Dockerfile

This example assumes you have a Python script named app.py and a requirements.txt file containing the dependencies for your application.

1. Open a terminal.
2. Navigate to the directory where you want to create or edit the Dockerfile.
3. Type vi Dockerfile and press Enter. This will open the vi editor with a new file named Dockerfile.
4. Press i to enter insert mode. You can now start typing your Dockerfile contents.
5. Once you’re done editing, press Esc to exit insert mode. Type :wq and press Enter to save the changes and exit vi. If you want to exit without saving, type :q! and press Enter

# For Python
----------------------------------------------------------------
#Use an official Python runtime as a parent image

FROM python:3.9-slim

#Set the working directory in the container

WORKDIR /app

#Copy the current directory contents into the container at /app

COPY . /app

#Install any needed dependencies specified in requirements.txt

RUN pip install --no-cache-dir -r requirements.txt

#Make port 8080 available to the world outside this container

EXPOSE 8080

#Define environment variable

ENV Username admin

#Run app.py when the container launches

CMD ["python", "app.py"]

----------------------------------------------------------------

# Build the Dockerfile
docker build -t my-python-app .

# Run the image
docker run -p 8080:8080 my-python-app


# For NodeJS
----------------------------------------------------------------
#Use an official Node.js runtime as a parent image

FROM node:14-alpine

#Set the working directory in the container

WORKDIR /usr/src/app

#Copy package.json and package-lock.json to the container

COPY package*.json ./

#Install dependencies

RUN npm install

#Copy the rest of the application source code to the container

COPY . .

#Expose port 3000 to the outside world

EXPOSE 3000

#Define environment variable

ENV NODE_ENV=production

#Command to run the application

CMD ["node", "app.js"]

----------------------------------------------------------------

# Build the Dockerfile
docker build -t my-node-app .

# Run the image
docker run -p 3000:3000 my-node-app
