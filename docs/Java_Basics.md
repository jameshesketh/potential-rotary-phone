## Setting Up Java Development Environment (JDK) on Windows – User-Specific Configuration

This guide details how to set up the Java Development Kit (JDK) on Windows, focusing on a user-specific configuration. This means the changes will only apply to your account, avoiding potential conflicts with other users on the system.

**Step 1: Download and Install the JDK**

1.  **Download:** Go to either the [Oracle JDK](https://www.oracle.com/java/jdk/downloads/) or [OpenJDK](https://openjdk.org/) website.
2.  **Choose Installer:** Select the correct installer for your system architecture (e.g., `jdk-21_windows-x64_bin.exe`).
3.  **Install:** Run the installer and follow the prompts.  Accept the license agreement. You can choose the default installation path (e.g., `C:\Program Files\Java\jdk-<version>`), *or customize it to a location like `C:\dev\jdk-<version>`*.

**Step 2: Configure User Environment Variables**

1.  **Access System Properties:** Search for "Environment Variables" in the Windows search bar and select "Edit the system environment variables."
2.  **<span class="delve __shimmer__">User Variables</span> Section:** In the "System Properties" window, click the "Environment Variables..." button. Focus on the **"User variables for [Your Username]"** section (not "<span class="delve __shimmer__">System variables</span>").

**3. Create/Edit <span class="delve __shimmer__">JAVA_HOME</span>**

*   **If `JAVA_HOME` exists:** Select it and click "Edit...".
*   **If `JAVA_HOME` does not exist:** Click "New...".
    *   **Variable name:** Enter `JAVA_HOME`.
    *   **Variable value:** Enter the **full path to your <span class="delve __shimmer__">JDK installation directory</span>**. For example: `C:\dev\jdk-21` (Replace `jdk-21` with your specific JDK version).

**4. Edit the `Path` Variable**

*   In the "User variables" section, locate the `Path` variable. Select it and click "Edit...".
*   Click "New" and add the path to the `bin` directory of your JDK installation. For example: `C:\dev\jdk-21\bin`. This allows you to run Java commands from the command line.
*   If there are other entries in the `Path` variable, ensure that the Java path is included.

**Step 3: Apply Changes and Verify**

1.  **Apply Changes:** Click "OK" on all open windows to save the changes.
2.  **Restart <span class="delve __shimmer__">Command Prompt</span>/Terminal:** Close and reopen any existing command prompt or terminal windows. This is **crucial** for the changes to take effect. The new environment variables are loaded only when a new shell session is started.

**Step 4: Verification**

After restarting the command prompt, verify that the environment variables are set correctly by running the following commands:

*   `echo %JAVA_HOME%` (should display the path you set)
*   <span class="delve __shimmer__">`java -version`</span> (should display the version of the Java runtime you expect)
*   <span class="delve __shimmer__">`javac -version`</span> (should display the version of the Java compiler you expect)

**Important Notes:**

*   **User vs. System Variables:** Setting variables in the "User variables" section only affects your user account. Setting them in "System variables" affects all users on the system, requiring administrator privileges.
*   **Order in PATH:** The order of entries in the `Path` variable can matter. If you have multiple Java versions installed, the version listed earlier in the path will take precedence.
*   **<span class="delve __shimmer__">WSL Integration</span>:** If you're using Windows Subsystem for Linux (WSL), verify that the `JAVA_HOME` path within WSL is also aligned with the "dev" directory on your Windows file system.
*   **<span class="delve __shimmer__">Custom Installation Location</span>:** If you installed the JDK to a non-standard location (e.g., `C:\dev\jdk-21`), ensure that the `JAVA_HOME` and `Path` variables reflect this custom path.


## Change the version of Java for IntelliJ Community Edition ##

Here's how to change the Java version used by IntelliJ IDEA Community Edition:

*   **Access Project Structure:** Navigate to `Ctrl + Shift + Alt + S` to open the Project Structure settings. This is the primary method for configuring Java versions within your IntelliJ projects.
*   **Select or Add a JDK:** Within Project Structure, locate the section for configuring your JDK (Java Development Kit). You’ll have the option to either select a JDK that's already been added to IntelliJ, or to add a new one if the version you want to use isn’t currently listed.
*   **Project SDK:** Once you've added or selected the desired JDK, ensure it's set as the "Project SDK" in the Project Structure settings. This tells IntelliJ which Java version to use for compiling and running your projects.
*   **IDE Boot JDK:** It's important to note that changing the Project SDK only affects the Java version used *within* IntelliJ for your projects. It does *not* change the Java version that IntelliJ itself runs on. If you need to change the Java version IntelliJ uses to operate, you’ll need to adjust the IDE Boot JDK settings separately.
*   **Platform Specifics:** The precise steps might vary slightly depending on your operating system (Windows, macOS, Linux), but the core process of using the Project Structure settings to select or add a JDK remains consistent.
*   **Restart if Necessary:** In some cases, you may need to restart IntelliJ IDEA for the changes to take effect fully.
*   **Verify the Change:** After making the changes, it's a good practice to verify that the correct Java version is being used by running a simple Java program or checking the project settings.

## Simple Java Class for displaying Important Java fields ##

```java
public class JavaVersionCheck {

    public static void main(String[] args) {
        System.out.println("Java Version: " + System.getProperty("java.version"));
        System.out.println("Java Runtime Version: " + System.getProperty("java.runtime.version"));
        System.out.println("Java Home: " + System.getProperty("java.home"));
        System.out.println("Java Vendor: " + System.getProperty("java.vendor"));
    }
}
```

**Explanation:**

*   **`public class JavaVersionCheck`**:  This declares a public class named `JavaVersionCheck`.
*   **`public static void main(String[] args)`**: This is the main method, the entry point of the program.
*   **`System.getProperty("java.version")`**:  This retrieves the Java version string (e.g., "17.0.2").  `System.getProperty()` is a standard Java method for getting system-level properties.
*   **`System.getProperty("java.runtime.version")`**:  Gets the version of the Java runtime environment.
*   **`System.getProperty("java.home")`**: Gets the directory where the Java runtime is installed. Useful for confirming the correct installation is being used.
*   **`System.getProperty("java.vendor")`**: Gets the vendor of the Java runtime (e.g., "Oracle Corporation", "Adoptium").
*   **`System.out.println(...)`**: Prints the retrieved version information to the console.

**How to Run:**

1.  **Save the Code:** Save the code as a file named `JavaVersionCheck.java`.
2.  **Compile:** Open a terminal or command prompt, navigate to the directory where you saved the file, and compile the code using the Java compiler:

    ```bash
    javac JavaVersionCheck.class
    ```

3.  **Run:** Execute the compiled class file:

    ```bash
    java JavaVersionCheck
    ```

The output will display the Java version, runtime version, home directory, and vendor currently being used.  This is a quick way to confirm that IntelliJ is indeed running your code with the expected Java version.




