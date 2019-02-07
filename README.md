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

