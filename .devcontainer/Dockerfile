# Use a base image with Java and any other dependencies required for your project
FROM adoptopenjdk:11-jdk-hotspot

# Set the working directory inside the container
WORKDIR /workspace

# Copy the project files into the container
COPY . .

# Set environment variables if needed
ENV ENV_VAR_NAME=VALUE

# Install Gradle
RUN apt-get update && \
    apt-get install -y wget unzip && \
    wget -q https://services.gradle.org/distributions/gradle-7.2-bin.zip && \
    unzip -q gradle-7.2-bin.zip -d /opt && \
    rm gradle-7.2-bin.zip

# Set Gradle environment variables
ENV GRADLE_HOME=/opt/gradle-7.2
ENV PATH=$PATH:$GRADLE_HOME/bin

# Run Gradle build
RUN gradle build

# Expose any necessary ports for your application
EXPOSE 8080

# Define the command to run your application
CMD ["java", "-jar", "your-application.jar"]
