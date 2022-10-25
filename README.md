Terraform Azure Template
=========================

Initial Terraform template for Azure IaC projects
--------------------------------------------------

This repository intends to be a pattern, a start, to create a modular infrastructure-as-code project using Terraform in Azure, following the best practices when using Storage Account remote backend for Terraform states. 

**remote_state** directory contains a Terraform and Azure CLI project to create a remote backend infrastructure containing:

**init.sh** (or *make init-proj* command) will:


## Project file structure

```
```

This template was created to be used with Terraform modules, stored in *modules* directory, and the root module must contains only necessary variables, outputs, data, locals and module calls. You can use your own Terraform modules with this template. 

## Pre-reqs

- An Azure subscription
- Configured environment to access Azure subscription
- az-cli
- Terraform
- Jinja2
- Git
- make
- Bash

## Usage Instructions

### Execution

1. Clone this repository
```
git clone https://github.com/mrbitsdcf/terraform_azure_template.git my-new-supercool-project
```

2. Remove Git configurations
```
cd my-new-supercook-project
rm -rf .git
```

3. Init Git repository with your own configurations
```
git init -b main
git config user.name 'My Name'
git config user.email 'my.email@somewhere.com'
git remote add origin URL
```

4. Configure variables in *init.sh*

The variables *KEY_NAME* and *PREFIX* must be configured to reflect actual values for Terraform statefile name and project name, i.e.: 

```
KEY_NAME="remote-state-project"
PREFIX="project"
```

5. Init the project
```
make init-proj
```

### Using Makefile

We have a Makefile as Terraform interface, with the following commands:

```
⇒  make
Terraform Makefile

clean                          Erase all project. VERY DESTRUCTIVE!
console                        Enter terraform console
destroy                        Prepare tfplan to destroy resources
dry-run                        Prepare tfplan to update resources
init                           Init terraform
init-proj                      Init Azure Storage Accounts for tfstate and configure backend
lint                           Lint HCL
run                            Apply tfplan
security                       Run tfsec validation
show                           Show state
validate                       Validate syntax

```

Command *init-proj* corresponds to execute script *init.sh*.

Command *clean* corresponds to execute script *cleanup.sh*.

Command *destroy* executes ```terraform plan``` with *-destroy* and save it to *tfplan* file. To really destroy entire launched infrastructure, execute ```make run```.

## How to contribute

Please read CONTRIBUTING.md guide

## Licensing

Please read MIT-LICENSE.txt. It's 2022.
