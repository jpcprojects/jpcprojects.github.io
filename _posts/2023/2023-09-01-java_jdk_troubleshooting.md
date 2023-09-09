---
title: Troubleshooting 'java --version' Issue After JDK 11 Installation
date: 2023-09-01
categories: [java, jdk]
tags: [java, jdk]
---

![Java JDK](/assets/img/posts/2023/java_jdk_troubleshooting/java_jdk_troubleshooting.jpg)


So, you've successfully installed JDK 11 on your Windows machine, but when you try to check the Java version using the `java --version` command, it doesn't seem to work. No need to worry; this is a common issue related to environment variables, and we're here to help you resolve it. In this blog post, we'll guide you through the troubleshooting steps to ensure that the `java` command works as expected.

## Troubleshooting Steps

Follow these steps to troubleshoot and resolve the `java --version` issue after installing JDK 11:

1 **Check JDK Installation Directory**:
   - Verify the installation directory of JDK 11. By default, it should be something like `C:\Program Files\Java\jdk-11.x.x`.

2 **Check System Environment Variables**:
   - Press Win + S and search for "Environment Variables."
   - Click on "Edit the system environment variables."
   - In the "System Properties" window, click the "Environment Variables" button.

3 **Create JAVA_HOME Variable**:
   - Under "System variables," check if you have a variable named JAVA_HOME. If not, create one:
     - Click "New" under System variables.
     - Set Variable name to `JAVA_HOME`.
     - Set Variable value to the installation path of JDK 11 (e.g., `C:\Program Files\Java\jdk-11.x.x`).

4 **Update Path Variable**:
   - In the same "Environment Variables" window, locate the Path variable under "System variables."
   - Select "Path" and click "Edit."
   - Add a new entry: `%JAVA_HOME%\bin`. This ensures that the 'java' executable is found when you run the command.

5 **Restart Your Command Prompt**:
   - If you had a command prompt open before setting the environment variables, close it and open a new one. This ensures that the updated environment variables take effect.

6 **Check 'java' Command**:
   - Ensure that you are running the `java` command without any typos or case sensitivity issues. It should be `java`, not `Java`.

7 **Verify Environment Variables**:
   - You can verify that the environment variables are set correctly by opening a new command prompt and running:
     ```
     echo %JAVA_HOME%
     ```

If you've followed these steps carefully and in order, you should now be able to run the `java --version` command and see the expected Java version information.

If, for any reason, you are still encountering issues, there might be other factors at play, such as conflicts with other software or potential system misconfigurations. In such cases, it might be helpful to seek assistance from someone with experience in troubleshooting software installation and environment variable issues.

## Additional Resources

For more detailed information and troubleshooting tips, consider exploring the following resource:

📝 [Oracle's Java SE Documentation](https://docs.oracle.com/en/java/javase/11/): The official documentation provides comprehensive guides and troubleshooting advice for Java SE, including installation and environment variables.

