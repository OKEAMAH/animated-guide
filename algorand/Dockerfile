# syntax=docker.io/docker/dockerfile:1.3@sha256:42399d4635eddd7a9b8a24be879d2f9a930d0ed040a61324cfdf59ef1357b3b2
FROM const-gen AS const-export
FROM docker.io/python:3.10@sha256:d719cce3399b609511e3a8f0e7171bb45a63cce24c14084ea33d705e162745fd

RUN python3 -m pip install virtualenv

RUN apt-get update
RUN apt-get -y install netcat

COPY Pipfile.lock Pipfile.lock
COPY Pipfile Pipfile

RUN python3 -m pip install pipenv
RUN pipenv install
RUN mkdir teal

COPY *.py .
COPY test/*.json .
COPY deploy.sh deploy.sh 
COPY --from=const-export .env .env
