FROM jenkins/jenkins:lts

USER root

# Install necessary packages for the Docker client
RUN apt-get update -qq && \
    apt-get install -y --no-install-recommends \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg2 \
    lsb-release \
    && rm -rf /var/lib/apt/lists/*

# Install Docker CLI
RUN curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add - && \
    echo "deb [arch=$(dpkg --print-architecture)] https://download.docker.com/linux/debian $(lsb_release -cs) stable" > /etc/apt/sources.list.d/docker.list && \
    apt-get update -qq && \
    apt-get install -y docker-ce-cli && \
    rm -rf /var/lib/apt/lists/*

# Add jenkins user to the docker group
RUN usermod -aG docker jenkins

# Switch back to the jenkins user
USER jenkins




# docker run -d \
#   --name jenkins \
#   -v /var/run/docker.sock:/var/run/docker.sock \
#   -v jenkins_home:/var/jenkins_home \
#   your-jenkins-image


# This file creates a Jenkins image that contains the Docker CLI
