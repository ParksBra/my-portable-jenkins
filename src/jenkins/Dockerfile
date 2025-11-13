FROM jenkins/jenkins:lts
USER root
RUN apt-get update
RUN apt-get install -y python3-full python3-pip python3-venv git

ADD ./requirements.txt /tmp/requirements.txt
RUN python3 -m venv /opt/master-venv
RUN /opt/master-venv/bin/pip install -r /tmp/requirements.txt
