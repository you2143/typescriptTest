FROM node:14.16.1-alpine3.10

WORKDIR /usr/src/app

RUN apk update && \
    apk upgrade && \
    apk add git && \
    npm install -g npm

ENV HOST 0.0.0.0
EXPOSE 3000

CMD [ "node", "app.js" ]