FROM openjdk:11 AS BUILD_IMAGE
RUN apt update && apt install maven -y
RUN git clone -b containers https://github.com/EmmanuelMoshood/e-project.git
RUN cd e-project &&  mvn install 

FROM tomcat:9-jre11
LABEL "Project"="eprofile"
LABEL "Author"="Emman"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
