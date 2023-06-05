# env0 Checkov Plugin

This env0 Checkov Plugin will allow you to run `checkov` scans on an IaC directory as a part of your custom flow. To use this plugin, you will need to use version 2 of `env0.yml`.

You can specify a particular version of Checkov to use by adding `checkov_version` to the inputs of the action in your env0.yml. If `checkov_version` is not specified or is set to "latest", the plugin will use the latest version of Checkov.

## Inputs

The Checkov plugin accepts the following inputs:

* `directory` (required) - The path to the directory with the IaC code to scan (the root folder is your project's root folder).
* `flags` - A string containing additional flags as one string.
* `checkov_version` (optional) - The version of Checkov to install. If not specified or "latest", the latest version is installed.

## Example Usage

In this example we will run a `checkov` scan on our tf folder before the "Terraform Plan" step of a deploy, using Checkov version 2.2.105. We will call that step "My Step Name":

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
            checkov_version: 2.2.105

```

## Further Reading

You can read more about `checkov` and the available flags [here](https://www.checkov.io/2.Basics/CLI%20Command%20Reference.html#cli-command-reference).
