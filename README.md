# Docker Build and Push GitHub Action

This GitHub Action is designed for building and pushing Docker images using Docker Buildx. It's particularly useful for CI/CD pipelines that require Docker image creation and deployment.



## Inputs

Below are the inputs required by the Docker Build and Push action:

- `registry`: The URL of the container registry where the image should be pushed (e.g., Docker Hub, GitHub Container Registry).
- `username`: The username for logging into the container registry.
- `password`: The password or token for logging into the container registry.
- `dockerfile-path`: The path to the Dockerfile within the repository.
- `context-path`: The Docker build context path (usually the directory containing the Dockerfile).
- `build-args`: Additional build arguments required for building the Docker image.
- `image-tags`: Comma-separated list of tags to be applied to the built Docker image.
- `no-cache`: Set to 'true' if you want to build the image without using the cache. Default is 'true'.
- `push-image`: Set to 'true' if the built image should be pushed to the registry. Default is 'true'.



## Usage

To use this action in your workflows, add the following step:

```yaml
- name: Build and Push Docker Image
  uses: your-github-username/docker-build-and-push-action@version
  with:
    registry: ${{ secrets.REGISTRY_URL }} # If you are using a private registry
    username: ${{ secrets.REGISTRY_USERNAME }}
    password: ${{ secrets.REGISTRY_PASSWORD }}
    dockerfile-path: './Dockerfile'
    context-path: '.'
    build-args: 'ARG1=value1,ARG2=value2'
    image-tags: 'myusername/myimage:latest'
    no-cache: 'true'
    push-image: 'true'
```


## Additional Information

- This action sets up Docker context and Docker Buildx before proceeding with the Docker image build and push.
- It is recommended to use this action with GitHub secrets to securely handle your credentials.
- For detailed usage of Docker Buildx and build arguments, refer to the official Docker documentation.
