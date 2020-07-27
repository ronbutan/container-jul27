# this is image will be based on Node 14
FROM node:14

# building the image
# environment variables to define my workspace
ENV APP_DIR=/app
ENV APP_PORT=3000
ENV DB_PORT=3306
ENV DB_USER=root
ENV DB_PASSWORD=changeit

# create and CD into APP_DIR
# mkdir /app
# cd /app
WORKDIR ${APP_DIR}

# copy the file from fortunr into /app
# ADD local image
# copy the files
ADD main.js .
ADD package.json .
ADD package-lock.json .
# copy the directories
ADD config config
ADD public public
ADD views views

# install dependencies - package.json
RUN npm install

# running the image
# Add heanlth check
HEALTHCHECK --interval=30s --timeout=5s --start-period=10s --retries=3 \
CMD curl -s -f http://localhost:${APP_PORT}/health || exit 1

# the port the application is exposing
EXPOSE ${APP_PORT}

# run the application
ENTRYPOINT [ "node", "main.js" ]