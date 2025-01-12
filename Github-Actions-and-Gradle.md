# Steps to configure java with gradle using github actions for continous integration and deployment (CI/CD):

  1. On GitHub, navigate to the main page of the repository.
  2. Under your repository name, click  Actions.
  3. The "Choose a workflow" page shows a selection of recommended workflow templates. Search for "Java with Gradle".
  4. On the "Java with Gradle" workflow, click Configure. This workflow performs the following steps:
  5. Checks out a copy of project's repository.
  6. Sets up the Java JDK.
  7. Sets up the Gradle environment. The gradle/actions/setup-gradle action takes care of caching state between workflow runs, and provides a detailed summary of all Gradle executions.
  8. The "Build with Gradle" step executes the build task using the Gradle Wrapper.
  9. Edit the workflow as required. For example, change the Java version.
  10. Click Commit changes.
  11. The gradle.yml workflow file is added to the .github/workflows directory of your repository.

## Example gradle.yml file:
```
name: Java CI with Gradle

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  build:

    runs-on: ubuntu-latest
    permissions:
      contents: read

    steps:
    - uses: actions/checkout@v4
    - name: Set up JDK 23
      uses: actions/setup-java@v4
      with:
        java-version: '23'
        distribution: 'temurin'

    - name: Setup Gradle
      uses: gradle/actions/setup-gradle@af1da67850ed9a4cedd57bfd976089dd991e2582 # v4.0.0

    - name: Build with Gradle Wrapper
      run: ./gradlew build

    - name: Upload build artifacts
      uses: actions/upload-artifact@v4
      with:
        name: Package
        path: build/libs

  dependency-submission:

    runs-on: ubuntu-latest
    permissions:
      contents: write

    steps:
    - uses: actions/checkout@v4
    - name: Set up JDK 23
      uses: actions/setup-java@v4
      with:
        java-version: '23'
        distribution: 'temurin'

    - name: Generate and submit dependency graph
      uses: gradle/actions/dependency-submission@af1da67850ed9a4cedd57bfd976089dd991e2582 # v4.0.0
```


Resource:
[Building and testing Java with Gradle](https://docs.github.com/en/actions/use-cases-and-examples/building-and-testing/building-and-testing-java-with-gradle)
