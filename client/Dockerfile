# stage 1
FROM node:alpine as builder 
WORKDIR /app
COPY package.json .
COPY package-lock .
COPY . .
RUN npm install
RUN npm build
CMD [ "npm","start" ]



