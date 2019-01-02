# CircleCI Trial Checklist
This checklist is a guide to making the most of your CircleCI trial. Managing DevOps tools can be complex, so we want to help you understand the full potential of CircleCI so that you can make an informed decision.


## &#9744; Set up a CircleCI account
Head to [https://circleci.com/signup](https://circleci.com/signup). Click on the “Sign Up” button for whichever VCS provider you would like to use with CircleCI. Sign in with you VCS login and authorize CircleCI to access your repositories.


## &#9744; Add a project to CircleCI
:page_facing_up: [__Full _Projects and Builds_ documentation__](https://circleci.com/docs/2.0/project-build/#section=getting-started)

1. On the left navigation bar, click “Add Projects”. The list automatically populates with the repositories in your VCS organization. You can search for projects using the “Filter projects…” search bar. If you are setting up a macOS project, click on the “macOS” tab.
2. If you aren’t seeing the correct repositories, make sure you are operating in the correct organization. You can switch between your organizations using the drop down in the top left corner.
3. Click “Set Up Project” next to the project you want to add to CircleCI.
4. On the next screen select the operating system and language for the project. And then copy the sample configuration code.
5. In a new browser tab, log in to your VCS, and navigate to the repository that you are setting up.
6. In the root directory of the repository, create a new directory named `.circleci`
7. Inside the `.circleci` folder, create a new file named `config.yml`
8. Paste the sample configuration code into the `config.yml` file and commit it to your master branch
9. Return to CircleCI and click “Start Building”
10. You should be taken to your first build, and you can see the logs from the execution environment


## &#9744; Install the CircleCI CLI
The CircleCI CLI allows you to run CircleCI actions locally, such as valitating your config file, running local builds, and operating on Orbs. Visit [this documentation](https://circleci.com/docs/2.0/local-cli/#section=configuration) for instructions on installing and using the CircleCI CLI.


## &#9744; Read our docs
While reading documentation isn't always the most exciting part of using CircleCI, it is the best way to become acquainted with the ins-and-outs of its capabilities. We would encourage you to spend some time digging through our [documentation library](https://circleci.com/docs) on your own, but below are some notable pieces to get you started:


### General

:page_facing_up: [CircleCI configuration reference](https://circleci.com/docs/2.0/configuration-reference/#section=configuration) -- The configuration reference is a blueprint of everything you can include in your `config.yml` file. This is your go-to document whenever you're not sure what options you have when writing your config.yml file.


:page_facing_up: [Introduction to YAML](https://circleci.com/docs/2.0/writing-yaml/#section=configuration) -- If you're entirely new to writing YAML configuration, we put together a cheatsheet to get you started.


### Workflow structure

:page_facing_up: [Overview of Workflows, Jobs, and Steps](https://circleci.com/docs/2.0/jobs-steps/) -- _Workflows, Jobs, and Steps_ are the building blocs of your CircleCI configuration. This document gives an overview of what they are, and how you should use them. You can find more information on configuring workflows in the [Workflows section](https://circleci.com/docs/2.0/configuration-reference/#workflows) of the configuration reference.


### Executors and images

:page_facing_up: [Executors and images overview](https://circleci.com/docs/2.0/executor-intro/#section=configuration) -- CircleCI offers highly customizable executor options so you can be sure that your testing environment matches your production environment. You can set up your build environment to run with the `docker`, `machine`, or `macos` executor, and specify an image with only the tools and packages you need.


#### Docker

:page_facing_up: [Docker executor overview](https://circleci.com/docs/2.0/executor-types/#using-docker) -- CircleCI has a first class integration with Docker, allowing you to build in any Docker image and run any Docker command natively.

:page_facing_up: [Learn about CircleCI Docker images](https://circleci.com/docs/2.0/circleci-images/#section=configuration) -- If you don't have an existing Docker image to run your jobs with, CircleCI has a library of prebuilt Docker images that you can pull into any of your jobs.

:page_facing_up: [Custom Docker image documentation](https://circleci.com/docs/2.0/custom-images/#section=configuration) -- If you'd like to build a custom Docker image to run your jobs, you can use `docker build` natively in CircleCI to do so.

:page_facing_up: [Using private Docker images](https://circleci.com/docs/2.0/private-images/#section=configuration) -- Also, if you already have Docker images built, but they are private, you can use your Docker credentials in CircleCI to pull these images.


#### Machine

:page_facing_up: [Get started with the Machine executor](https://circleci.com/docs/2.0/executor-types/#using-machine) -- Using the `machine` executor runs your job in a dedicated, ephemeral virtual machine. This gives your application full access to operating system resources and gives you full control over the execution environment.


#### MacOS

:page_facing_up: [Get started with the macOS executor](https://circleci.com/docs/2.0/executor-types/#using-macos) -- If your building a macOS application, you'll need to use the macOS executor. When you use the `macOS` executor, you'll also define which Xcode version you want to use.


## &#9744; Update your `config.yml` file

Once you've read through our documentation, spend some time updating your configuration to optimize it for your project. Here are a few questions to ask yourself when doing so:

1. Does your workflow optimize for maximum parallelism? The more jobs you can run asynchronously, the quicker your workflow will finish. Here is an [example config](https://circleci.com/docs/2.0/sample-config/#sample-configuration-with-parallel-jobs) with parallel jobs.
2. Are you running any jobs that are building very slowly? You can declare a more powerful [`resource_class`](https://circleci.com/docs/2.0/configuration-reference/#resource_class) such as `medium+` or `large` for these jobs to make them run faster. Larger resource classes have more vCPUs and RAM. You can also declare a `resource_class: small` for lightweight jobs like code health checks to save credits. There is no secret sauce here for choosing the right resource class, but experimenting can help you optimize your workflows over time.
3. Do you have commands, jobs, or executors that are repeated in your config? For any of these, you should create reusable components using top level keys:

```YAML
commands:
  reusable-command-1:
    # Create a reusable command here. A reusable command can be called as a step in a job.

jobs:
  reusable-job-1:
    # Create a reusable job here. A reusable job can be used in a workflow.

executors:
  reusable-executor-1:
    # Create a reusable executor here. Reusable executors can be called as the executor for any job.
```

4. Could any of your commands, jobs, or executors be reused in other projects? If so, you may want to [create an orb](#creating-orbs) that defines them.


## &#9744; Rerun a failed job with SSH for debugging

If one of your jobs fails, one of the best ways to debug it is to SSH into it's container as it is running. You can do this by rerunning any failed job with SSH.

To rerun a job with SSH, open the job in the CircleCI UI, then, in the upper right corner of the page, click the arrow next to the _"Rerun workflow"_ button and select _"Rerun job with SSH"_.

<img src="/img/rerun-ssh.png" width="200px" />

From your CLI on your machine, SSH into the build using the information provided in the CircleCI UI. Happy debugging!


## &#9744; Explore Orbs

[Orbs](https://circleci.com/orbs) are reusable, sharable packages of CircleCI configuration. Orbs allow you to import pre-build commands, jobs, and executors into your configuration file, so that you don't spend time reinventing the wheel.

### Using existing orbs

Our ecosystem is already full of existing orbs built by our community. Have a look through the [Orbs Registry](https://circleci.com/orbs/registry) to see if any existing orbs could simplify your configuration. If want to learn more about using existing orbs, [read our documentation](https://circleci.com/docs/2.0/using-orbs/#section=configuration).

### Creating Orbs

If you have a use case for an orb that hasn't been created yet, it's easy to build it yourself so that you can use it across all of your projects. [Read our documentation](https://circleci.com/docs/2.0/creating-orbs/#section=configuration) on creating orbs to get started.

**Note** - At this time _all_ orbs are public, meaning that anyone can see their source or use them in a project. Make sure to follow best practices and parameterize any secrets your orb may use so that they are not published in your orb's source code.
