# Use the official Jenkins image as the base image
FROM jenkins/jenkins:lts

# Switch to the root user to install Python and Node.js
USER root

# Update the package list and install Python, Node.js, Newman, and Robot Framework
RUN apt-get update && \
    apt-get install -y python3 python3-pip curl && \
    apt-get install -y nodejs && \
    npm install -g newman && \
    pip3 install robotframework && \
    pip3 install robotframework-jsonlibrary &&\
    rm -rf /var/lib/apt/lists/*

# Switch back to the jenkins user
USER jenkins

# Print Python, Newman, and Robot Framework versions to verify installation
RUN python3 --version && pip3 --version && newman --version && robot --version
