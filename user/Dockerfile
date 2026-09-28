# FROM node:20-alpine3.21
# WORKDIR /opt/server
# COPY package.json .
# COPY *.js  .
# RUN npm install
# ENV MONGO="true" \
#     REDIS_URl="redis://redis:6379" \
#     MONGO_URL="mongodb://mongodb:27017/users"
# CMD ["node", "server.js"]



FROM node:20-alpine3.21 AS builder
WORKDIR /opt/server
COPY package.json .
COPY *.js .
RUN npm install

FROM node:20-alpine3.21
WORKDIR /opt/server
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop && \
    chown -R roboshop:roboshop /opt/server
ENV MONGO="true" \
    REDIS_URL="redis://redis:6379" \
    MONGO_URL="mongodb://mongodb:27017/users"
COPY --from=builder /opt/server  /opt/server
USER roboshop
CMD ["node" , "server.js"]    





