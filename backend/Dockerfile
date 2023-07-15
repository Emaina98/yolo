# stage 1 dockerfile-syntax
FROM node:16-alpine
WORKDIR /app
COPY package.json .
COPY . .
RUN npm install
EXPOSE 5001
CMD [ "npm","run","start" ]

