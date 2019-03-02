FROM willfarrell/codeship-base

# Install aws cli and supporting cli

# https://pypi.org/project/awscli/
ARG awscli=1.16.109
# https://github.com/aws/amazon-ecs-cli
# Pushing docker images to ECR
# Pushing docker-compose files to ECS
ARG ecs-cli=1.12.1

RUN apk add --no-cache --virtual .deps python groff && \
    apk add --no-cache --virtual .build-deps py-pip curl && \
    pip install --upgrade \
        awscli==${awscli} \
        python-magic && \
    curl https://s3.amazonaws.com/amazon-ecs-cli/ecs-cli-linux-amd64-v${ecs-cli} > /usr/local/bin/ecs-cli && \
    apk -v --purge del .build-deps

# TODO verify ecs-cli signature
