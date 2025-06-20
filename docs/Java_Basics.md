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



