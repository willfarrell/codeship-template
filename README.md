# codeship-template
Docker images for CI/CD process

## Workflows
### React
```
init -> node -> aws
```
### serverless
```
init -> node -> aws
```
### ECS
```
init -> docker -> aws
```
### terraform
```
init -> terraform -> [Approve] -> terraform
```

## Containers
### init
Decrypts env files and extends with GIT ENV

### docker

### node
setup up NPM_TOKEN, if needed then runs:
```bash
npm ci
npm outdated
npm audit
npm run lint
npm test
```

### aws
Contains the `aws-sdk cli`.

## TODO
- docs
  - `jet` basics
  - env encryption
- Phase I:
  - static assets
  - serverless
- Phase II:
  - docker
  - terraform
- Phase III
  - terraform module aws-code-pipeline


## `env`
```bash
# Setup ENV
AES_PASSWORD=


# Build NodeJS
NPM_TOKEN=


# Build Docker
DOCKER_REGISTRY=
DOCKER_USERNAME=
DOCKER_PASSWORD=

# Deploy
AWS_REGION=
AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
```

## `env.{development,teesting,staging,production}`
```bash
# React
REACT_APP_COMMIT_HASH=${GIT_COMMIT_HASH}
REACT_APP_VERSION=

# awscli
# TODO assume roles ENV
AWS_ACCOUNT_ID=
AWS_ASSUME_ROLE=
```
