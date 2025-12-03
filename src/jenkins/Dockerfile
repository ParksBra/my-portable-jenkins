FROM jenkins/jenkins:lts
USER root

# Install Python 3 and other dependencies
RUN apt-get update
RUN apt-get install -y python3-full python3-pip python3-venv git

# Create parent virtual environment
ADD ./requirements.txt /tmp/requirements.txt
RUN python3 -m venv /opt/master-venv
RUN /opt/master-venv/bin/pip install -r /tmp/requirements.txt

# Install Terraform
RUN apt-get install -y apt-transport-https ca-certificates curl gpg lsb-release
RUN curl https://apt.releases.hashicorp.com/gpg | gpg --dearmor | tee /usr/share/keyrings/hashicorp-archive-keyring.gpg > /dev/null
RUN echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(grep -oP '(?<=UBUNTU_CODENAME=).*' /etc/os-release || lsb_release -cs) main" | tee /etc/apt/sources.list.d/hashicorp.list
RUN apt-get update
RUN apt-get install -y terraform
