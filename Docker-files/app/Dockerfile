FROM openjdk:11 AS BUILD_IMAGE
RUN apt update && apt install maven && apt install git -y
RUN git clone https://github.com/Akshay-source/Vprofile-containerized.git
RUN cd Vprofile-containerized && mvn install

FROM tomcat:9-jre11
LABEL Author="Akshay"
LABEL Project="Vprofile"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE Vprofile-containerized/target/vprofile-v2.war  /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD [ "catalina.sh", "run" ]