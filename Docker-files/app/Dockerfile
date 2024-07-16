FROM openjdk:11 AS Build_IMAGE
RUN apt-get update && apt-get install -y maven
Run git clone https://github.com/soibi10/vprofile-project.git
run cd vprofile-project && git checkout docker && mvn install

FROM tomcat:9-jre11
LABEL "project"="vprofile"
LABEL "Author"="Soibi10"

run rm -rf /usr/local/tomcat/webapps/*
copy --from=Build_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

expose 8080

cmd ["catalina.sh", "run"]
