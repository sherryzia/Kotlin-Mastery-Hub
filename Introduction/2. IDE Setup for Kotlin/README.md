### Setting up IntelliJ IDEA for Kotlin

IntelliJ IDEA is one of the most popular IDEs for Kotlin development, offering robust support for Kotlin as it is developed by JetBrains, the creators of Kotlin.

#### Steps to Set Up IntelliJ IDEA for Kotlin:
1. **Download and Install IntelliJ IDEA**:
   - Go to the [IntelliJ IDEA official website](https://www.jetbrains.com/idea/download/).
   - Choose the **Community Edition** (free version) or **Ultimate Edition** (for advanced features).
   - Download the installer based on your OS (Windows, macOS, Linux).
   - Follow the instructions for installation.

2. **Start IntelliJ IDEA and Create a New Project**:
   - Launch IntelliJ IDEA.
   - On the welcome screen, click on **New Project**.

3. **Select Kotlin as the Project Type**:
   - In the "New Project" window, under **Languages**, select **Kotlin**.
   - Choose **JVM** as the framework for Kotlin.
   - Make sure **Kotlin/JVM** is selected under the **Build System** (you can choose Gradle, Maven, or IntelliJ's default).
   - Click **Next**.

4. **Configure the Project Settings**:
   - Name your project (e.g., "KotlinIntroduction").
   - Set the project location where you want it to be saved.
   - Specify the JDK. If the JDK is not installed, click **Download JDK** to install it.
   - Click **Finish** to create the project.

5. **Create a Kotlin File**:
   - Once the project is created, right-click on the `src` folder in the Project panel.
   - Select **New** > **Kotlin File/Class**.
   - Name the file (e.g., `Main.kt`), and choose **File**.
   
6. **Write Your First Kotlin Code**:
   - Inside the newly created Kotlin file, write your first program:

     ```kotlin
     fun main() {
         println("Hello, Kotlin!")
     }
     ```

7. **Run the Program**:
   - Click the green play button in the toolbar or right-click the Kotlin file and select **Run 'MainKt'**.
   - The output "Hello, Kotlin!" should appear in the Run panel.
