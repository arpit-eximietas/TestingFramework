FROM jenkins/jenkins:2.452.1-jdk17
USER root

# Install necessary dependencies
RUN apt-get update && \
    apt-get install -y lsb-release \
                       gnupg \
                       curl \
                       sudo \
                       python3-venv \
                       python3-pip

# Install Docker dependencies and repository
RUN curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg && \
    echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian $(lsb_release -cs) stable" > /etc/apt/sources.list.d/docker.list

# Install Docker
RUN apt-get update && \
    apt-get install -y docker-ce-cli

# Create and activate virtual environment
RUN python3 -m venv /opt/venv
ENV PATH="/opt/venv/bin:$PATH"

# Install Robot Framework
RUN pip install --upgrade pip && \
    pip install robotframework

# Install Jenkins plugins including Blue Ocean and Docker Pipeline
USER jenkins
RUN jenkins-plugin-cli --plugins "blueocean docker-workflow"
