# Build multi architectural docker images via GitHub Actions

## Requirements

- A GitHub account to fork the repository and configure GitHub Actions.
- A Docker account to create and manage Docker images.
- Access to a web browser and internet connection.

## Presentation

You can [download the presentation slides here](docs/githubactions.pdf).

## Steps

### Create a New GitHub Repository as a Fork

1. Navigate to the [workshop-github-actions repository](https://github.com/ArmDeveloperEcosystem/workshop-github-actions/).
2. Click the **Fork** button in the top-right corner of the page.
3. In the **Create a fork** dialog:
    - Select your GitHub account or organization where you want to create the fork.
    - Optionally, provide a name for the forked repository (default is `workshop-github-actions`).
    - Click **Create fork**.

### Retrieve Your Docker Username and Password

1. **Docker Username**:  
    Your Docker username is the name you use to log in to [Docker Hub](https://hub.docker.com/).

2. **Docker Personal Access Token**:  
    - Log in to [Docker Hub](https://hub.docker.com/).
    - Navigate to your account settings.
    - Go to Personal Access Token
    - Click on **Create Access Token**.
    - Provide a name for the token (e.g., `github-actions-token`).
    - Select the desired expiration date for the token.
    - Under **Access Permissions**, ensure you grant **read & write** access to repositories.
    - Click **Generate** and copy the token.  
    **Note**: Make sure to save the token securely as it will not be shown again.

### Add Variables to GitHub Actions

1. Go to your GitHub repository.
2. Click on the **Settings** tab.
3. In the left sidebar, select **Secrets and variables** > **Actions**.
4. Click the **New repository secret** button.
5. Add the following secrets:
    - `DOCKER_PAT`: Your Docker Personal Access Token we generated above.
6. Move from the **Secrets** tab to the **Variables** tab
7. Click the **New repository variable** button.
8. Add the following variables:
    - `DOCKER_USER`: Your Docker username.
    - `BASE_OS`: `ubuntu-24.04`

### Run the GitHub Actions Workflow

1. Go to the `Actions` page for your GitHub repository.
2. Trigger the `image-build.yml` workflow manually:
    - The workflow is located at [`.github/workflows/image-build.yml`](.github/workflows/image-build.yml)
    - From the `Actions` page, click **Run workflow**.
3. Monitor the workflow execution:
    - Check the progress and logs in the **Actions** tab.
    - Ensure the workflow completes successfully without errors.

Once the workflow finishes, your multi-architecture Docker images will be built and pushed to Docker Hub.
