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

