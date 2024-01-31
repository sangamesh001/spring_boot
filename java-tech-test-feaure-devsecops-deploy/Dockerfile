# Use amazoncorretto as the base image with a build argument for the version
ARG CORRETTO_VERSION=17
FROM amazoncorretto:${CORRETTO_VERSION}


# Set environment variables
ENV MAVEN_VERSION=3.9.6
ENV MAVEN_HOME=/opt/maven
ENV PATH ${MAVEN_HOME}/bin:${PATH}

# Install necessary tools

RUN yum install -y tar gzip

# Download and install Maven
RUN curl -fsSL https://downloads.apache.org/maven/maven-3/${MAVEN_VERSION}/binaries/apache-maven-${MAVEN_VERSION}-bin.tar.gz -o /tmp/apache-maven.tar.gz \
    && tar -xzf /tmp/apache-maven.tar.gz -C /opt \
     && ln -s /opt/apache-maven-${MAVEN_VERSION} ${MAVEN_HOME}

# Create and set the working directory

WORKDIR /tmp/
# Copy the project files into the container
COPY pom.xml /tmp/

COPY src /tmp/src/

# Build the application using Maven
RUN mvn package
# Expose the port that your Spring Boot application will run on
EXPOSE 8080
# Command to run the Spring Boot application
CMD [ "mvn", "spring-boot:run" ]