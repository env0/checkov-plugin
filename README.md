# env0 Checkov Plugin

  

This env0 Checkov Plugin will allow you to run `checkov` scans on an IaC directory as a part of your custom flow. To use this plugin, you will need to use version 2 of `env0.yml`.

  

We are using Checkov version `2.2.105`

  

## Inputs

  

The Checkov plugin accepts the following inputs:

* path (required) - the path to the directory with the IaC code to scan (the root folder is your project's root folder)

* flags - a string containing additional flags as one string


## Example Usage

  

In this example we will run `checkov` scan on our tf folder before the "Terraform Plan" step of a deploy. We will call that step "My Step Name":

```yaml
version: 2
deploy:
  steps:
    terraformPlan:
      before:
        - name: My Step Name # The name that will be presented in the UI for this step
          use: https://github.com/env0/env0-checkov-plugin
          inputs:
            directory: .
            flags: --framework terraform 

```

  

## Further Reading

You can read more about `checkov` and the available flags [here](https://www.checkov.io/2.Basics/CLI%20Command%20Reference.html#cli-command-reference).
