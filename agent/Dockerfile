FROM debian:buster-slim

RUN apt-get update && \
    apt-get install -y \
      build-essential \
      curl \
      file \
      git \
      python3-pip && \
    rm -rf /var/lib/apt/lists/*

COPY ["ssh", "/root/.ssh"]

ARG AWS_CLI=1.18.21
RUN pip3 install awscli~="$AWS_CLI" --upgrade
ARG SAM_CLI=0.44.0
RUN pip3 install aws-sam-cli~="$SAM_CLI" --upgrade

ARG COMMIT
ENV BUILDKITE_ABOUT_IMAGE "keithduncan/sam-agent\ncommit: $COMMIT\n\naws-cli: $AWS_CLI\naws-sam-cli: $SAM_CLI"