# Gradle-Tutorial

Run the command `gradle wrapper` to automatically install the gradle/wrapper files and gradlew and gradlew.bat files. 

When configuring Gradle for a project and preparing to add it to a repository, you'll want to include all necessary files that define the build configuration, dependencies, and settings. Here's a list of files and directories you should include in your repository:

### Essential Gradle Files
1. **`build.gradle` (or `build.gradle.kts` for Kotlin DSL)**  
   - This is the main build configuration file for your project. It contains information about dependencies, plugins, tasks, and other project-specific configurations.

2. **`settings.gradle` (or `settings.gradle.kts` for Kotlin DSL)**  
   - Used to define the project's structure and include any subprojects (in multi-module projects).

3. **`gradle.properties`**  
   - Optional file for defining global properties and configurations for your Gradle build (e.g., JVM options, environment variables).

4. **`gradlew`**  
   - The Gradle wrapper script for Linux/macOS. It allows anyone to build your project without needing to have Gradle pre-installed.

5. **`gradlew.bat`**  
   - The Gradle wrapper script for Windows.

6. **`gradle/wrapper/gradle-wrapper.jar`**  
   - The Gradle wrapper executable JAR file. This ensures that the correct version of Gradle is downloaded and used.

7. **`gradle/wrapper/gradle-wrapper.properties`**  
   - Configuration file for the Gradle wrapper, specifying the Gradle version and distribution type (e.g., binary-only or complete).

### Optional Files and Directories
1. **Custom Scripts or Configuration Files**  
   - If you have custom build scripts or task definitions in separate files (e.g., `custom-script.gradle`), include them.

2. **`.idea/` or `.vscode/`** (Optional for IDE-specific configurations)  
   - Include only if you want to share IDE configurations, though it's better to exclude these using `.gitignore`.

3. **Plugin Configuration Files**  
   - Files like `checkstyle.xml` or `spotbugs.xml` if you're using plugins that require custom configurations.

### Exclude These Files
1. **Generated Build Artifacts**  
   - Exclude the `build/` directory, which contains compiled classes, JAR files, and other generated outputs.
   
2. **Local Configurations**  
   - Exclude `*.iml` files or other IDE-specific files unless explicitly necessary.

3. **Gradle Cache**  
   - Exclude the `.gradle/` directory in the root of your project, as it contains cached dependencies and metadata.

### Example `.gitignore` for Gradle Projects
```plaintext
# Gradle
.gradle/
build/

# IntelliJ IDEA
*.iml
.idea/
out/

# VS Code
.vscode/

# OS-specific files
.DS_Store
Thumbs.db
```

By including the above essential files and directories, you ensure that your Gradle setup is portable and can be used by anyone cloning your repository.


You can create a continuous integration (CI) workflow in GitHub Actions to build and test your Java project with Gradle. [Building and testing Java with Gradle](https://docs.github.com/en/actions/use-cases-and-examples/building-and-testing/building-and-testing-java-with-gradle)
