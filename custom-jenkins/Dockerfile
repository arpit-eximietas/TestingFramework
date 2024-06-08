FROM jenkins/jenkins:2.452.1-jdk17
USER root

# Install necessary dependencies
RUN apt-get update && \
    apt-get install -y lsb-release \
                       gnupg \
                       curl \
                       sudo \
                       python3-venv \
                       python3-pip \
                       nodejs \
                       npm

# Create and activate virtual environment
RUN python3 -m venv /opt/venv
ENV PATH="/opt/venv/bin:$PATH"

# Install Robot Framework and JSONLibrary
RUN pip install --upgrade pip && \
    pip install robotframework \
                robotframework-jsonlibrary

# Install Newman
RUN npm install -g newman
RUN npm install -g newman-reporter-htmlextra

# Install Jenkins plugins including Blue Ocean
USER jenkins
RUN jenkins-plugin-cli --plugins "blueocean"
