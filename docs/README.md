# codeship-template
Docker images for CI/CD process and how to get started.

## Getting Started

### Prerequisites
- [Docker](https://www.docker.com/get-started)
- [Codeship Jet CLI](https://documentation.codeship.com/pro/jet-cli/installation/)

### Basics
- `codeship.aes` is the password for decrypting `env.encrypted`
- `codeship-services.yml` contains the containers you're going to use
- `codeship-steps.yml` contains the build/deploy orchestration 
- You can run the CI/CD locally with `jet steps`

## Deployment Workflows
### Static Assets (Angular/React/Vue) -> AWS S3
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
### init [CI]
Collection of re-usable scripts

### docker [CI]
Everything you need to build, scan, and push to any repository.

### node [CI]
setup up NPM_TOKEN, if needed then runs:
```bash
npm ci
npm outdated
npm audit
npm run lint
npm test
```

### aws [CD]
Contains the `aws-sdk cli`.

### terraform [CD]
Contains the `terraform cli`


## Docker Registries
How to set up a repository to receive the built docker image. It is suggested to create a bot user just for CI purposes.

### Docker Hub/Cloud
1. Got to [Repositories](https://cloud.docker.com/u/)
1. Press `Create Repository`
1. Enter `Name` & `Description` and press `Create`
1. Press `Collaborators` and add the id of the user that will be running the builds

### AWS ECR
1. Add the following to your `terraform`
```hcl-terraform
resource "aws_ecr_repository" "foo" {
  name = "bar"
}
output "ecr_repository_url" {
  value = "${aws_ecr_repository.foo.repository_url}"
}
```
2. Copy the url into your `env.encrypted`


## Built With

* [CodeShip Jet CLI](https://documentation.codeship.com/pro/jet-cli/usage-overview/) - CI/CD CLI
* [Docker](http://www.dropwizard.io/1.0.2/docs/) - Linux Containers
* [HashiCorp Terraform](https://www.terraform.io/) - Infrastructure as Code

<!--
## Contributing

Please read [CONTRIBUTING.md](https://gist.github.com/PurpleBooth/b24679402957c63ec426) for details on our code of conduct, and the process for submitting pull requests to us.
-->
## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/willfarrell/codeship-template/tags). 

## Authors

* **will Farrell** - *Initial work* - [willfarrell](https://github.com/willfarrell)

See also the list of [contributors](https://github.com/willfarrell/codeship-template/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details


## TODO
- Phase I:
  - static assets
  - serverless
- Phase II:
  - docker
  - ECS
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
