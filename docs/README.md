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
- You can encrypt your `env` file by running `jet encrypt env env.encrypted`

### `.gitignore`
```bash
# CI/CD
.env
env*
codeship.aes
!*.encrypted
.tmp
```

### What you need
Copy the following files from `/docs/samples` into the root of your repo.
- `codeship-services.yml`
- `codeship-steps.{one of}.yml`
- `env`

## Deployment Workflows
### Static Assets (Angular/React/Vue) -> AWS S3
### serverless -> AWS
### docker -> AWS ECS
### terraform


## Containers
### scripts
Collection of re-usable scripts

### docker
Everything you need to build, scan, and push to any repository.

### node


### aws
Contains the `aws-sdk cli`.

### terraform
Contains the `terraform cli`

## Scripts

### Global
- **setup-env:**
  - **setup-environment:**
  - **setup-gitflow:**

### Android


### AWS
- **aws-env-check:** Checks that the necessary `env` are set to execute `aws-*` scripts.
- **aws-auth:** Sets credentials to allow connection to AWS.
- **aws-s3-deploy:** Deploys static assets to a S3 bucket.

### docker
- **docker-env-check:** Checks that the necessary `env` are set to execute `docker-*` scripts.
- **docker-auth:** Sets credentials to allow connection to private docker registry.
- **docker-build:** Builds docker image and pushes to registry.

### npm
- **npm-env-check:** Checks that the necessary `env` are set to execute `npm-*` scripts.
- **npm-auth:** Sets credentials to allow connection to private npm registry.
- **npm-version:** Pull version from `package.json` and applies to `env`.

### terraform
- **terraform-:** TODO


## Built With

* [CodeShip Jet](https://documentation.codeship.com/pro/jet-cli/usage-overview/) - CI/CD CLI
* [Docker](http://www.dropwizard.io/1.0.2/docs/) - Linux Containers
* [HashiCorp Terraform](https://www.terraform.io/) - Infrastructure as Code

## Contributing

Please read [CONTRIBUTING.md](https://www.contributor-covenant.org/version/1/4/code-of-conduct) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/willfarrell/codeship-template/tags). 

## Authors

* **will Farrell** - *Initial work* - [willfarrell](https://github.com/willfarrell)

See also the list of [contributors](https://github.com/willfarrell/codeship-template/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details


## TODO
- Phase I:
  - [x] static assets
  - [x] serverless
- Phase II:
  - [x] docker
  - [ ] ECS
  - [x] terraform
- Phase III
  - [ ] terraform module aws-code-pipeline
- [ ] ensure all images have a USER line
