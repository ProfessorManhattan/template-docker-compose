## Docker Compose / Stack Project

We house most of our Docker Compose / Stack configurations in our [Ansible Docker Swarm role](https://github.com/megabyte-labs/ansible-swarm). However, when a stack is more complicated and might need to include other files (i.e. Terraform files, or special configuration files) then we dedicate a repository to the project.

Unlike our [Dockerfile](https://gitlab.com/megabyte-labs/templates/docker) repository projects, we do not have a strict repository style guide. There are, however, a few things to keep in mind.

Docker Compose / Stack configurations are supposed to be easy to use, one-liner ways of launching otherwise somewhat complicated networks. So if the repository is not launchable by just running `docker up -d docker-compose.yml` then a file called `launch.sh` should be included in the repository. The `launch.sh` file should make setting up the stack a one-liner process.

### Docker Containers

If the stack requires containers that are not from reputible sources or if the stack would benefit from having custom Dockerfile container builds then each Dockerfile should have its own repository in the appropriate sub-group in the [Docker group](https://gitlab.com/megabyte-labs/docker). Please also look over the [README of our Dockerfile boilerplate](https://gitlab.com/megabyte-labs/template/docker).

### Configuration Management

In order to make the experience truly simple and adhere to the one-liner principle, it may be required to incorporate some sort of configuration management strategy. This should be done by either using Ansible or Terraform. In cases where performance is vital, Saltstack can be used as well.

The configuration choices should be thorough and automatically apply the settings that would satisfy the needs of most users. The configurations should make a best-effort at integrating with the other software we include in [Gas Station](https://github.com/megabyte-labs/Gas-Station), [JumpUSB](https://jumpusb.com), and any platform/service that a typical GitHub power-user would have in their stack.

That all said, the most important part of the project is to understand and have an intuitive feel for the stack's requirements.
