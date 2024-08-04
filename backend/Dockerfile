    FROM node:18 AS builder

    WORKDIR /usr/src/app

    COPY package.json ./
    COPY yarn.lock ./

    RUN npx yarn

    COPY .sailsrc .
    COPY app.js .
    COPY api ./api
    COPY config ./config
    COPY public ./public
    COPY views ./views

    FROM node:18

    WORKDIR /usr/src/app
    COPY --from=builder /usr/src/app/ /usr/src/app/

    # # Switch to root user to install global packages
    USER root
    RUN npm install -g nodemon

    EXPOSE 1337
    # # Switch back to non-root user
    USER node


    CMD [ "nodemon", "app.js" ]
    # CMD [ "node", "app.js" ]