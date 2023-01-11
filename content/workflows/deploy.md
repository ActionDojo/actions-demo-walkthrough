<h1>Continuous Deployment (CD)</h1>

<h3>Continuous Deployment (CD) is a development practice in which code changes are automatically built, tested, and deployed to production as soon as they are committed to the repo. This allows organizations to deliver new features and updates more quickly, and reduces the risk of errors and downtime. Continuous Deployment is an extension of Continuous Integration, and typically involves additional automation and testing to ensure that code changes are safe to deploy to production.

To demonstrate the concept, we'll practice deploying a static portfolio website to GitHub Pages. In a typical software project you would be deploying a dynamic application to your cloud provider of choice – like Azure, AWS or GCP.</h3>


<h3>Here are the steps to automatically deploy a website to GitHub Pages using Actions:

1. Create a new file in your repository called `.github/workflows/deploy.yml`. This file will define your deployment workflow.

2. In the YAML file, specify the name of your workflow and the trigger for the workflow. Like this:

    ```yml
    name: Deploy
    on:
    push:
        branches:
        - production
    ```
    This will trigger the workflow every time you push code to the "production" branch of your repository.


3. Define the jobs that will be run as part of the workflow. A job is a series of steps that are run in a specific environment. For our deployment workflow, we will only need one job. Here's the code block for defining the deployment job:

    ```yml
    jobs:
    deploy:
        runs-on: ubuntu-latest
        steps:
        - uses: actions/checkout@v2
        - name: Deploy to GitHub Pages
        uses: JamesIves/github-pages-deploy-action@3.8.1
        with:
            ACCESS_TOKEN: ${{ secrets.ACCESS_TOKEN }}
            BRANCH: gh-pages
            FOLDER: build
    ```
    In this example, we are defining a job called deploy that runs on the ubuntu-latest environment. It has two steps:

    - `actions/checkout@v2`: This step checks out your code from the repository.
    - `JamesIves/github-pages-deploy-action@3.8.1`: This step is a GitHub Action that deploys a website to GitHub Pages. The with block specifies the following options:
    - `ACCESS_TOKEN`: This is a GitHub secret that contains an access token with permission to push code to the repository.
    - `BRANCH`: This is the name of the branch that the website should be deployed to (in this case, gh-pages).
    - `FOLDER`: This is the name of the folder that contains the built website (in this case, build).

4. Here's the whole workflow file:

    ```yml
    name: Deploy
    on:
    push:
        branches:
        - production

    jobs:
    deploy:
        runs-on: ubuntu-latest
        steps:
        - uses: actions/checkout@v2
        - name: Deploy to GitHub Pages
        uses: JamesIves/github-pages-deploy-action@3.8.1
        with:
            ACCESS_TOKEN: ${{ secrets.ACCESS_TOKEN }}
            BRANCH: gh-pages
            FOLDER: build
    ```
    To see your workflow run: push your changes, go to the Actions tab in GitHub, and click on the workflow run associated with this file.