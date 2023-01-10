<h1>Continuous Integration (CI) Workflows</h1>

<h2>What is CI?</h2>
<h3>Continuous Integration (CI) is a software development practice where developers regularly merge their code changes to the repository. This allows teams to detect and fix errors quickly, as well as automate the build, test, and deployment process. CI can improve the quality of software and reduce the time it takes to deliver new features to users.

We'll build a simple CI workflow that scans your code for linting errors whenever someone pushes code or submits a pull request to the repository.

<details>
<summary><h2>What does "linting" mean?</h2></summary>
A linting workflow is a series of steps that are run to check code for style and syntax errors. Linting ensures that code is consistent and follows best practices.

The specific steps included in a linting workflow can vary, but they may include things like checking for syntax errors, enforcing coding style guidelines, checking for formatting issues, and ensuring that code is correctly structured.

Linters are typically run automatically as part of a Continuous Integration (CI) process, and the results of the linting checks are typically displayed in the CI pipeline. This allows developers to identify and fix linting issues as they work, rather than waiting until later on in the process.

Overall, the purpose of a linting workflow is to help improve the quality and maintainability of the code in a repository.
</details>

Alright, let's get started!
</h3>

<h3>

1. First, create a new file in your repository called `.github/workflows/linter.yml`. This file will define your linting workflow.

2. Next, specify the name of your workflow and the trigger for the workflow. For example:
    ```yml
    name: Lint
    on: [push, pull_request]
    ```
    This triggers the workflow any time there's a push or pull request to the repository.

3. Now, we'll define the jobs that will be run as part of the workflow. A job is a series of steps that are run in a specific environment. For our linting workflow, we will only need one job. You can define that job like this:

    ```yml
    jobs:
    lint:
        runs-on: ubuntu-latest
        steps:
        - uses: actions/checkout@v2
        - uses: github/super-linter@v2
        with:
            args: "--enable all"
    ```

4. 
    In this example, we are defining a job called Lint that runs on the ubuntu-latest environment(standard GitHub-hosted runners on 2-core Linux machines). It has two steps:
    - `actions/checkout@v2`: This step checks out your code from the repository.

    - `github/super-linter@v2`: This step runs the Super Linter action, which lints your code using a variety of different linters. The `with` block specifies that we want to enable all of the available linters.

    The `- uses` keyword is followed by the name of the action and its version (specified using the @ symbol). In this case, an action is being run from the GitHub Actions Marketplace. You can also run actions from other sources that you've defined within your repository, organization or enterprise.

    The `with` block specifies any additional options or configurations for the action. In this case, the args option is being used to specify that all of the available linters should be enabled.

5. Here's the whole workflow file:

    ```yml
    name: Lint
    on: [push, pull_request]

    jobs:
    lint:
        runs-on: ubuntu-latest
        steps:
        - uses: actions/checkout@v2
        - uses: github/super-linter@v2
        with:
            args: "--enable all"
    ```
    To see your workflow run: push your changes, go to the Actions tab in GitHub, and click on the workflow run associated with this file.

<br/><br/><br/>