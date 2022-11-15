FROM node:19-alpine as dependencies
WORKDIR /usr/src/app
COPY package.json .
RUN npm install

FROM node:19-alpine
WORKDIR /usr/src/app
RUN apk update && apk add bash
COPY package.json .
COPY wait-for-it.sh .
COPY src ./src
COPY --from=dependencies /usr/src/app/node_modules ./node_modules
EXPOSE 3000