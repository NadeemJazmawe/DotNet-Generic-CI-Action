
# .NET Core CI GitHub Action

This GitHub Action runs a CI process for .NET repositories, both single and mono repos.

## Inputs

### `dotnet-version`

**Required** The version of .NET Core to use. Default is `6.0.x`. This input is required to ensure that the correct version of .NET Core is used for the CI process. It allows developers to specify the desired version or use the default version if not specified.

## Example usage

```yaml
name: .NET Core CI

on:
    push:
        branches: 
            - '**'
    pull_request:
        branches: 
            - '**'

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
            run: dotnet build --no-restore --configuration Release

        - name: Run tests
            run: dotnet test --no-build --verbosity normal --configuration Release
```
