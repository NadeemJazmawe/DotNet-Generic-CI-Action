# GitHub Action: .NET Core Workflow


## Overview

This GitHub Action facilitates the setup, build, and testing of .NET Core projects within your CI/CD pipeline. It defines a series of steps to manage the .NET Core environment and execute essential commands for your project.

![GitHub Action Diagram](https://github.com/NadeemJazmawe/DotNet-Generic-CI-Action/blob/main/images/action-diagram.png)

## High-Level Design

### Metadata Section

- **name**: The name of the GitHub Action.
- **description**: A brief description of what the action does.
- **author**: The author of the action.

### Inputs Section

- **dotnet-version**: An input parameter to specify the .NET Core version. This is a required parameter and has a default value.

### Runs Section

- **using**: Specifies the type of action (composite in this case).
- **steps**: A list of steps to be executed by the action.

## Detailed YAML Structure

### Metadata Section

- **name**: Specifies the name of the action.
- **description**: Provides a brief description of the action.
- **author**: Indicates the author of the action.

### Inputs Section

- **dotnet-version**: Defines an input parameter for the .NET Core version. It is required and defaults to `6.0.x`.

### Runs Section

- **using**: Specifies that the action uses a composite run step.
- **steps**: Lists the steps to be executed:
  1. **Checkout code**: Uses the `actions/checkout@v2` action to check out the repository code.
  2. **Setup .NET Core**: Uses the `actions/setup-dotnet@v1` action to set up the specified .NET Core version.
  3. **Restore dependencies**: Runs the `dotnet restore` command to restore dependencies.
  4. **Build**: Runs the `dotnet build` command to build the project.
  5. **Run tests**: Runs the `dotnet test` command to execute the tests.

## Usage

To use this GitHub Action in your repository, include the following in your workflow YAML file:

```yaml
name: .NET Core Workflow

on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Setup .NET Core
        uses: actions/setup-dotnet@v1
        with:
          dotnet-version: '6.0.x'

      - name: Restore dependencies
        run: dotnet restore

      - name: Build
        run: dotnet build --no-restore

      - name: Run tests
        run: dotnet test --no-build --verbosity normal
```

## Contributing
If you have suggestions for improvements or encounter issues, please feel free to open an issue or submit a pull request.

## License
This project is licensed under the MIT License.


This `README.md` provides a clear and detailed overview of the GitHub Action, including its design, structure, and usage instructions. Adjust the content as needed to fit your specific implementation and requirements.



