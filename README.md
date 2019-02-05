# codeship-template
Docker images for CI/CD process

## Workflows
### React
```
init -> node -> awscli
```
### serverless
```
init -> node -> awscli
```
### ECS
```
init -> docker -> awscli
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
- bootstrap with codeship
- docs: `jet` basics
- docs: env encryption
