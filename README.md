# CircleCI Trial Checklist
This checklist is a guide to making the most of your CircleCI trial. Managing DevOps tools can be complex, so we want to help you understand the full potential of CircleCI so that you can make an informed decision.


## &#9744; Set up a CircleCI account
Head to [https://circleci.com/signup](https://circleci.com/signup). Click on the “Sign Up” button for whichever VCS provider you would like to use with CircleCI. Sign in with you VCS login and authorize CircleCI to access your repositories.


## &#9744; Add a project to CircleCI
:page_facing_up: __Full _Projects and Builds_ documentation__

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

:page_facing_up: [CircleCI configuration reference](https://circleci.com/docs/2.0/configuration-reference/#section=configuration)

The configuration reference is a blueprint of everything you can include in your `config.yml` file. This is your go-to document whenever you're not sure what options you have when writing your config.yml file.


:page_facing_up: [Introduction to YAML](https://circleci.com/docs/2.0/writing-yaml/#section=configuration)

If you're entirely new to writing YAML configuration, we put together a cheatsheet to get you started.


### Workflow structure

:page_facing_up: [Overview of Workflows, Jobs, and Steps](https://circleci.com/docs/2.0/jobs-steps/)

_Workflows, Jobs, and Steps_ are the building blocs of your CircleCI configuration. This document gives an overview of what they are, and how you should use them. You can find more information on configuring workflows in the [Workflows section](https://circleci.com/docs/2.0/configuration-reference/#workflows) of the configuration reference.


### Executors and images
CircleCI offers highly customizable executor options so you can be sure that your testing environment matches your production environment. You can set up your build environment to run with the `docker`, `machine`, or `macos` executor, and specify an image with only the tools and packages you need.

:page_facing_up: [Executors and images overview](https://circleci.com/docs/2.0/executor-intro/#section=configuration)


#### Docker

:page_facing_up: [Docker executor overview](https://circleci.com/docs/2.0/executor-types/#using-docker).
CircleCI has a first class integration with Docker, allowing you to build in any Docker image an run any Docker command natively.

:page_facing_up: [Learn about CircleCI Docker images](https://circleci.com/docs/2.0/circleci-images/#section=configuration).
If you don't have an existing Docker image to run your jobs with, CircleCI has a library of prebuilt Docker images that you can pull into any of your jobs.

:page_facing_up: [Custom Docker image documentation](https://circleci.com/docs/2.0/custom-images/#section=configuration)
If you'd like to build a custom Docker image to run your jobs, you can use `docker build` natively in CircleCI to do so.

:page_facing_up: [Using private Docker images](https://circleci.com/docs/2.0/private-images/#section=configuration)
Also, if you already have Docker images built, but they are private, you can use your Docker credentials in CircleCI to pull these images.


### Machine
Using the `machine` executor runs your job in a dedicated, ephemeral virtual machine. This gives your application full access to operating system resources and gives you full control over the execution environment.

You may want to use the `machine` executor if you need to use `ping` or modify system with `sysctl` commands.

The machine executor also allows you to build Docker images without downloading additional packages for languages like Ruby and PHP.

:page_facing_up: [Get started with the Machine executor](https://circleci.com/docs/2.0/executor-types/#using-machine)

### macOS
If your building a macOS application, you'll need to use the macOS executor. When you use the macOS executor, you'll also define which Xcode version you want to use.

:page_facing_up: [Get started with the macOS executor](https://circleci.com/docs/2.0/executor-types/#using-macos)
