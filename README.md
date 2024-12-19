# Argus Build Frontend

The **sunet-argus-frontend** is used to build a specific version of the code hosted in the [Argus Frontend GitHub repository](https://github.com/Uninett/Argus-frontend.git) https://github.com/Uninett/Argus-frontend.git.

To change the version being built, you can update the `.jenkins.yaml` file with the desired settings. For example:

```yaml
docker_tags:
- "v1.14.1_sunet-104e2c46"
docker_build_args: |
  BRANCH_NAME="v1.14.1"
  REPO_URL="https://github.com/Uninett/Argus-frontend.git"
```

### Key Points

- The `REPO_URL` should generally remain unchanged as it points to the main repository.
- The `BRANCH_NAME` should specify the tag version from the Uninett repository that you want to test.
- Update `docker_tags` to match the version you wish to use.

### Better Tag Selection

Alternatively, you can use the Python script `bump-tag.py` to automatically select a specific tag and update the `.jenkins.yaml` file. To do this, follow these steps:

```bash
chmod +x bump-tag.py
./bump-tag.py
```

This script simplifies the process by determining the appropriate tag to use and applying the changes to the `.jenkins.yaml` file and commiting the code. 
The python code should be used only after a successful commit

### Notes

Ensure that the selected tag in `BRANCH_NAME` matches a valid version from the Uninett repository. Properly updating the `docker_tags` and `BRANCH_NAME` ensures consistency between the build configurations and the repository version you intend to test.
