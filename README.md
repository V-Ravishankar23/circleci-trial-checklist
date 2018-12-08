# CircleCI Trial Checklist
This checklist is a guide to making the most of your CircleCI trial. Managing DevOps tools can be complex, so we want to help you understand the full potential of CircleCI so that you can make an informed decision.

## &#9744; Set up a CircleCI account
Head to [https://circleci.com/signup](https://circleci.com/signup). Click on the “Sign Up” button for whichever VCS provider you would like to use with CircleCI. Sign in with you VCS login and authorize CircleCI to access your repositories.

## &#9744; Add a project to CircleCI
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

## &#9744; Get to know your `config.yml` file
__*Note*__ Review the CircleCI [configuration reference](https://circleci.com/docs/2.0/configuration-reference/#section=configuration) to become acquainted with the ins-and-outs of our capabilities.

Writing CircleCI configuration may seem daunting, but once you learn the basics, you’ll be optimizing your builds in no time. CircleCI config is written in declarative YAML syntax. If you’re new to writing YAML, take a look at our [introduction to YAML docs](https://circleci.com/docs/2.0/writing-yaml/#section=configuration).

The power of CircleCI lies in your configuration. We have built our platform to be as unopinionated as possible so that CircleCI can be used to create the ideal CI/CD framework for any project. The more you are able to optimize your configuration for your unique project, the more you will get out of CircleCI. The first step in doing so is understanding the building blocks of your configuration file: _Workflows, Jobs, and Steps_.

```
Workflows
  ⤷ Jobs
    ⤷ Steps
```

__Key Documentation__
* Read [this documentation](https://circleci.com/docs/2.0/jobs-steps/) to gain a better understanding of Workflows, Jobs, and Steps__
* Review the [CircleCI configuration reference](https://circleci.com/docs/2.0/configuration-reference/#section=configuration)

## &#9744; Understand executors
CircleCI offers highly customizable executor options so you can be sure that your testing environment matches your production environment. You can set up your build environment to run with the `docker`, `machine`, or `macos` executor, and specify an image with only the tools and packages you need.

&#128279; [Executors and images overview](https://circleci.com/docs/2.0/executor-intro/#section=configuration)

### Docker
CircleCI has a first class integration with Docker, allowing you to run any Docker command natively inside a CircleCI build.


__Key Documentation:__
* [Executors and images overview](https://circleci.com/docs/2.0/executor-intro/#section=configuration)
* [Instructions on using Docker, Machine, and macOS executors](https://circleci.com/docs/2.0/executor-types/#using-docker)
