# VSCode Environment for Terraform Azure Provider Development

This Repo is to provide an isolated and low-configuration environment for Terraform Azure Providers. The goal is to get a developer adding provider features as quickly as possible.

VSCode Dev Container Includes:
* Go 1.16
* Terraform
* Az CLI
* Symlinked `.terraformrc`
* Use of `.env` file and a `setenv` command to set and update environment variables

## Getting Started

### 1. Repo Setup

1. Clone this repo and open in VSCode Dev Container.
2. Edit `.gitmodules` with your forked `terraform-provider-azurerm` repo clone URL (ssh or https)
3. Run `git submodule init`
4. Run `git submodule update`
5. You should know have content under the `terraform-provider-azurerm` folder

### 2. Set up Environment Variables

1. Run `az login` in the VSCode Dev Container terminal
2. Create a Service Principal with the subscription you want to use. Take note of the output.
3. Copy `.env.example` and Paste/Rename the new file as `.env`
4. Fill out the `.env` file with info from Step 2
5. Run `setenv`
6. Run `env` to verify that the values are correctly set in the environment variables

