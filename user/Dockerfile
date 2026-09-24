FROM node:20-alpine
WORKDIR /opt/server
COPY package.json /opt/server
#COPY *js  /opt/server   
#when coping to current directory we can give as "." which means current directory
RUN npm install
RUN apk upgarde && \
    apk add curl
ENV MONGO="true" \
    REDIS_URL="redis://redis:6379" \
    MONGO_URL="mongodb://mongodb:27017/users"
COPY *js  /opt/server    
CMD ["node" , "server.js"]
