FROM openjdk:11 AS BUILD_IMAGE
RUN apt update && apt install maven git -y
RUN git clone https://github.com/Harshad75/vprofile-project.git 
RUN cd vprofile-project && git checkout docker && mvn install 

FROM tomcat:9-jre11
LABEL "Project"="Vprofile"
LABEL "Author"="Harshad"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war
EXPOSE 8080
WORKDIR /usr/local/tomcat 
CMD ["catalina.sh", "run"]
