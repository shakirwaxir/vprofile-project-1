FROM openjdk:11 AS BUILD_IMAGE
RUN apt update && apt install maven -y
RUN git clone https://github.com/shakirwaxir/vprofile-project.git
Run cd vprofile-project && git checkout docker && mvn install

FROM tomcat:9.0-jre11
LABEL "Project"="Vprofile"
LABEL "Author"="Shakir"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]