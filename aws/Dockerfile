FROM willfarrell/codeship-base

# Install aws cli and supporting cli

# https://pypi.org/project/awscli/#history
ARG awscli=1.16.147
# https://github.com/aws/amazon-ecs-cli/releases
# Pushing docker images to ECR
# Pushing docker-compose files to ECS
ARG ecscli=1.14.1
# https://github.com/silinternational/ecs-deploy/releases
ARG ecsdeploy=3.6.0

RUN apk update && \
    apk add --no-cache --virtual .deps python groff && \
    apk add --no-cache --virtual .build-deps py-pip curl && \
    pip install --upgrade \
        awscli==${awscli} \
        python-magic && \
    curl https://s3.amazonaws.com/amazon-ecs-cli/ecs-cli-linux-amd64-v${ecscli} > /usr/local/bin/ecs-cli && \
    chmod +x /usr/local/bin/ecs-cli && \
    curl https://raw.githubusercontent.com/silinternational/ecs-deploy/${ecsdeploy}/ecs-deploy > /usr/local/bin/ecs-deploy && \
    chmod +x /usr/local/bin/ecs-deploy && \
    apk -v --purge del .build-deps
