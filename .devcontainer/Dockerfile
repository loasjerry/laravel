# Use a base image with Java and any other dependencies required for your project
FROM adoptopenjdk:11-jdk-hotspot

# Set the working directory inside the container
WORKDIR /workspace

# Copy the project files into the container
COPY . .

# Set environment variables if needed
ENV ENV_VAR_NAME=VALUE

# Install any additional dependencies or tools required for your project
RUN apt-get update && \
    apt-get install -y <package-name>

# Run any build or setup commands specific to your project
RUN ./gradlew build

# Expose any necessary ports for your application
EXPOSE 8080

# Define the command to run your application
CMD ["java", "-jar", "your-application.jar"]
