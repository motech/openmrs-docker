FROM google/debian:wheezy

ADD openmrs-runtime.properties /var/lib/tomcat7/openmrs-runtime.properties
ADD run.sh /root/run.sh
ADD openmrs_dump.sql /root/openmrs_dump.sql

RUN apt-get update; \
  apt-get install -y curl openjdk-7-jre tomcat7; \
  curl -L http://sourceforge.net/projects/openmrs/files/releases/OpenMRS_Platform_1.12.0/openmrs.war/download \
       -o /var/lib/tomcat7/webapps/openmrs.war; \
  mkdir /var/lib/OpenMRS; \
  mkdir /usr/share/tomcat7/.OpenMRS; \
  mkdir /usr/share/tomcat7/.OpenMRS/modules; \
  curl -L "https://drive.google.com/uc?export=download&id=0B4MuNrgt176HMG9VTTF4UnduYmM" \
       -o /usr/share/tomcat7/.OpenMRS/modules/webservices.rest-omod-2.17.SNAPSHOT.omod; \
  apt-get install -y mysql-server; \
  chown tomcat7:tomcat7 /var/lib/tomcat7/openmrs-runtime.properties /var/lib/OpenMRS /usr/share/tomcat7/.OpenMRS; \
  chmod +x /root/run.sh

EXPOSE 8080

CMD ["/root/run.sh"]
