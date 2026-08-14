
FROM maven:3.9.16 As builder

WORKDIR /app

COPY pom.xml .

COPY src ./src

RUN mvn clean package && \
    mv target/shipping-1.0.jar shipping.jar 

FROM eclipse-temurin:17-jre-alpine
EXPOSE 8080
WORKDIR /app

RUN addgroup -S roboshop && adduser -S -G roboshop roboshop && \
    chown -R roboshop:roboshop /app
COPY --from=builder /app/shipping.jar .
USER roboshop

CMD ["java", "-jar", "shipping.jar"]

# FROM maven:3.9.16

# WORKDIR /app

# COPY pom.xml .

# COPY src ./src

# RUN mvn clean package

# RUN mv target/shipping-1.0.jar shipping.jar 
# EXPOSE 8080
# CMD ["java", "-jar", "shipping.jar"]

