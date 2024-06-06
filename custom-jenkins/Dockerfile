# Use the official Jenkins image as the base image
FROM jenkins/jenkins:lts

# Switch to the root user to install Python
USER root

# Update the package list and install Python
RUN apt-get update && \
    apt-get install -y python3 python3-pip && \
    rm -rf /var/lib/apt/lists/*

# Switch back to the jenkins user
USER jenkins

# Print Python version to verify installation
RUN python3 --version && pip3 --version
