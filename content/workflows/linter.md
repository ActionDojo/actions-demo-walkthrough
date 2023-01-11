<h1>Linting - Continuous Integration</h1>

<h3>Continuous Integration (CI) is the practice of regularly merging your code changes to the repository. This allows teams to detect and fix errors quickly, as well as automate the build, test, and deployment process. CI can improve the quality of software and reduce the time it takes to deliver new features.

We'll build a simple CI workflow that scans your code for linting (syntax) errors whenever someone pushes code or submits a pull request to the "main" branch of the repository.

Let's get started!
</h3>

<h3>

1. First, create a new file in your repository called `.github/workflows/linter.yml`. This file will define your linting workflow.

2. Next, specify the name of your workflow and the trigger for the workflow. For example:
    ```yml
    name: Lint Code Base

    on:
    push:
        branches: [ "main" ]
    pull_request:
        branches: [ "main" ]
    ```
    This triggers the workflow any time there's a push or pull request to the "main" branch of the repository.

3. Now, we'll define the jobs that will be run as part of the workflow. A job is a series of steps that are run in a specific environment. For our linting workflow, we'll use one job with two steps. You can define it like this:

    ```yml
    jobs:
        run-lint:
            runs-on: ubuntu-latest
            steps:
            - name: Checkout code
                uses: actions/checkout@v3
                with:
                fetch-depth: 0

            - name: Lint Code Base
                uses: github/super-linter@v4
                env:
                VALIDATE_ALL_CODEBASE: false
                DEFAULT_BRANCH: "master"
                GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
    ```

4. In this example, we are defining a job called `run-lint` that runs on the ubuntu-latest environment(standard GitHub-hosted runners on 2-core Linux machines). It has two steps:
    
    1. `actions/checkout@v3`: This step checks out your code from the repository. The fetch-depth is set to 0, which means that the full git history will be pulled down.

    2. `github/super-linter@v4`: This step runs the Super Linter action, which lints your code using a variety of different linters. The `with` block specifies that we want to enable all of the available linters.

    The `- uses` keyword is followed by the name of the action being used and its version(specified using the @ symbol). In this case, an action is being run from the GitHub Actions Marketplace. You can also run actions that you've defined within your repository, or in other repositories in your organization/enterprise.

    - `VALIDATE_ALL_CODEBASE: false` – determines if the entire codebase should be linted or just the changed files. In this case it's just the changed file.
    - `DEFAULT_BRANCH: "master"` – the branch that should be used as the default branch for pull requests.
    - `GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}` – The GITHUB_TOKEN is an environment variable that is automatically set by GitHub and contains a token for authenticating with the GitHub API.

5. Here's the whole workflow file:

    ```yml
    name: Lint Code Base

    on:
    push:
        branches: [ "main" ]
    pull_request:
        branches: [ "main" ]

    jobs:
        run-lint:
            runs-on: ubuntu-latest
            steps:
            - name: Checkout code
                uses: actions/checkout@v3
                with:
                fetch-depth: 0

            - name: Lint Code Base
                uses: github/super-linter@v4
                env:
                VALIDATE_ALL_CODEBASE: false
                DEFAULT_BRANCH: "master"
                GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
    ```
    To see your workflow run: submit a pull request after making your changes, go to the Actions tab in GitHub, and click on the workflow run associated with this file. I'll explain how to do this in the next step.
    
    In summary, this GitHub action does linting of the codebase when a push or pull request is made against the main branch, by checking out the codebase and using super-linter, with a token for authentication.

<br/><br/><br/>