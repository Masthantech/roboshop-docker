FROM maven:3.9.16 as builder
WORKDIR /opt/server
COPY pom.xml .
RUN mvn clean package && \
    mv target/shipping-1.0.jar shipping.jar
COPY src /opt/server/src 

FROM eclipse-temurin:17-jre-alpine 
WORKDIR /opt/server
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop && \
    chown -R roboshop:roboshop /opt/server
ENV CART_ENDPOINT="cart:8080" \
    DB_HOST="mysql"    
COPY --from=builder  /opt/server/shipping.jar .
USER roboshop    
CMD ["java", "-jar" , "shipping.jar"]    






# FROM maven:4.0.0-rc-5-eclipse-temurin-26-alpine
# WORKDIR /opt/server
# COPY pom.xml .
# COPY src /opt/server/src
# RUN mvn clean package
# RUN mv /opt/server/target/shipping-1.0.jar /opt/server/shipping.jar
# ENV CART_ENDPOINT="cart:8080" \
#     DB_HOST="mysql"
# CMD ["java", "-jar", "shipping.jar"]     