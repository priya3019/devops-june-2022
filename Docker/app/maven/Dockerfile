FROM maven AS BUILD
WORKDIR /maven
COPY . /maven
COPY ./libraries /root/.m2
RUN mvn --version
RUN mvn clean package

FROM tomcat:8.0-alpine
COPY --from=BUILD /maven/target/calculator.war /usr/local/tomcat/webapps
CMD ["catalina.sh","run"]
