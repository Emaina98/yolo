



## Yolo Containerization README
This file contains the steps followed in the containerization of Yolo e-commerce website.
## Requirements
Make sure that you have the following installed::
#### Docker 
Docker is a containerization platform that enables you to build, distribute, and run containers.
## Getting Started
## Navigate to the Client Folder 
`cd client`
## Create Client Dockerfile
Create a file named 'Dockerfile' in the client directory. The Dockerfile defines the instructions to build the container image. 

## Frontend Dockerfile 

`FROM node:16-alpine
WORKDIR /app
COPY package.json .
COPY package-lock.json .
COPY . .
RUN npm install
CMD [ "npm","build" ]
RUN npm run build

#stage 2
FROM nginx:alpine
WORKDIR /usr/share/nginx/html
COPY --from=builder /app/build .`

## Build the Container Image
`docker build -t emaina98/clientyolo:v1 .`
## Run the Container
`docker run -p 3000:80 emaina98/clientyolo:v1`

Access the website by opening a web browser and navigating to http://localhost:3000

## Best Practices
Minimal base image used to reduce the container's size.
## Open a new terminal and repeat the same steps in the backend folder
 `cd backend`
## Create backend Dockerfile
Create a file named 'Dockerfile'in the client directory. The Dockerfile defines the instructions to build the container image. 
# backend dockerfile-syntax
`FROM node:16-alpine
WORKDIR /app
COPY package.json .
COPY . .
RUN npm install
EXPOSE 5000
CMD [ "npm","run","start" ]`
``
## Build the Container Image
`docker build -t emaina98/backend:v1.0.3  .`
## Run the Container
`docker run -p 5000:5000 emaina98/backend:v1.0.3`

Access the website by opening a web browser and navigating to http://localhost:5000