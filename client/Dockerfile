# stage 1
FROM node:16-alpine as builder
WORKDIR /app
COPY package.json .
COPY package-lock.json .
COPY . .
RUN npm install
EXPOSE 3000
CMD [ "npm","build" ]
RUN npm run build

# stage 2
FROM nginx:alpine
WORKDIR /usr/share/nginx/html
COPY --from=builder /app/build .


