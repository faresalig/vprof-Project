FROM openjdk:11 AS Build_Image
RUN apt update && apt install maven -y
RUN git clone https://github.com/hkhcoder/vprofile-project.git
RUN cd vprofile-project && git checkout containers && mvn install


FROM tomcat:9-jre11
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=Build_Image vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/Root.war

EXPOSE 8080

CMD [ "containers.sh" "run"]
