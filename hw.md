## 1. Create a GitHub Actions workflow

Create the workflow on the `main` branch. It must run only when changes are pushed to the `main` branch.

The workflow must have three separate jobs:

1. Build the application with Maven.
2. Create and publish a Docker image.
3. Verify the resulting Docker image.

### Notes

- Feel free to use the workflow created during the exercise as a starting point, or create the workflow differently.
- There is no need to publish with Maven this time because `pom.xml` is not ready for this.
- To build with Maven, the following command is sufficient:

  ```bash
  ./mvnw package
  ```

- The file `docker-build-and-publish.txt` contains the appropriate commands for building and publishing the Docker image. Copy those commands into your workflow file.
- Check the image name in that file and use the same name in your workflow. Replace `USERNAME` with your GitHub username.
- To verify the Docker image, start only the `verify-image.sh` script.
- Check the image name in that script as well and replace `USERNAME` with your GitHub username.
- If you want to start the application locally, follow the instructions in the repository’s `README` file.

## 2. Modify the application

Make these modifications according to Git best practices and the feature-branching strategy:

- Change the REST/HTTP endpoint from:

  ```text
  /application/test
  ```

  to:

  ```text
  /cubix/test
  ```

  Update `verify-image.sh` so that it calls the new, correct URL.

- Change the configured default message from:

  ```text
  default
  ```

  to:

  ```text
  This is a default message
  ```

- Update any available tests accordingly. Try building the application locally.

After making these changes, create pull requests for any new branches you used. Target your own forked repository’s `main` branch, not the original `drsylent` repository’s `main` branch. Accept the pull requests using any merge strategy, but do not delete the source branch.

## Hints

- You do not need to open the project in an IDE because only strings need to be replaced. Both changes are in:

  `src/main/java/hu/cubix/cloud/api/ApplicationController.java`

- You can make the modification directly on GitHub or in a simple text editor.
- If you are uncomfortable modifying the code yourself, copy the required changes from the final version in the `help` folder:

  - `help/ApplicationController.java` → `src/main/java/hu/cubix/cloud/api/ApplicationController.java`
  - `help/ApplicationControllerTest.java` → `src/test/java/hu/cubix/cloud/api/ApplicationControllerTest.java`
