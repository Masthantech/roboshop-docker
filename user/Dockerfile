FROM node:20-alpine3.21 as builder
WORKDIR /opt/server
COPY package.json .
COPY *.js .
RUN npm install

FROM node:20-apline3.21
WORKDIR /opt/server
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop && \
    chown -R roboshop:roboshop /opt/server
ENV MONGO="true" \
    REDIS_URL="redis://redis:6379" \
    MONGO_URL="mongodb://mongodb:27017/users"
COPY --from=builder /opt/server  /opt/server
USER roboshop
CMD ["node" , "server.js"]    




# FROM node:20-alpine
# WORKDIR /opt/server
# COPY package.json /opt/server
# #COPY *js  /opt/server   
# #when coping to current directory we can give as "." which means current directory
# RUN npm install
# ENV MONGO="true" \
#     REDIS_URL="redis://redis:6379" \
#     MONGO_URL="mongodb://mongodb:27017/users"
# COPY *js  /opt/server    
# CMD ["node" , "server.js"]
