FROM ubuntu:22.04 as builder

RUN apt update
RUN apt install openjdk-8-jdk -y
RUN apt install maven -y

WORKDIR words

COPY . .

RUN mvn verify


#FROM openjdk:21-ea-5
FROM alpine

RUN apk add openjdk8-jre-base
#openjdk9-jre-headless

EXPOSE 8080

WORKDIR words

COPY --from=builder /words/ .

# -> exec pour bien avoir le pid 1
CMD exec java -Xmx8m -Xms8m -jar target/words.jar