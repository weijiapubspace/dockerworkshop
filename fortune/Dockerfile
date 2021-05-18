FROM node:16

# env variables
ENV APP_ROOT=/app APP_PORT=3000

# cd to /app
WORKDIR ${APP_ROOT}

# copy the following files
ADD main.js .
ADD package.json .
ADD package-lock.json .

# copy folders need a name
ADD public public
ADD views views

# install packages in image
RUN npm i 

#document that this container listens on 3000
EXPOSE ${APP_PORT}

# health check
HEALTHCHECK --interval=30s --timeout=5s --start-period=5s --retries=3 \
    CMD curl -s -f http://localhost:${APP_PORT}/healthz || exit 1

# run application
ENTRYPOINT ["node", "main.js"]