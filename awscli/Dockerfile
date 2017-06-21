FROM alpine:latest
MAINTAINER Jessie Frazelle <jess@linux.com>
ENV awsuser aws

RUN apk --no-cache add \
	ca-certificates \
	groff \
	less \
	python \
	py2-pip \
	&& pip install awscli aws-shell\
  && adduser ${awsuser} -S -s /bin/sh \
	&& su ${awsuser} -c "mkdir -p /home/${awsuser}/.aws" \
	&& { \
		echo '[default]'; \
		echo 'output = json'; \
		echo 'region = $AWS_DEFAULT_REGION'; \
		echo 'aws_access_key_id = $AMAZON_ACCESS_KEY_ID'; \
		echo 'aws_secret_access_key = $AMAZON_SECRET_ACCESS_KEY'; \
	} > /home/${awsuser}/.aws/config

USER aws
ENTRYPOINT ["aws"]
