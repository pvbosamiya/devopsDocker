FROM ubuntu:16.04 

WORKDIR /mydir
RUN apt-get update && apt-get install -y curl
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash -
RUN apt-get install -y nodejs
RUN /usr/bin/node -v && /usr/bin/npm -v

COPY backend-example-docker .
RUN npm install

EXPOSE 8000

ENTRYPOINT [ "/usr/bin/npm", "start" ]
