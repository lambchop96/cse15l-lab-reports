# Week 1 Lab Report

This is a tutorial on how to remotely access the `ieng6` computers at UCSD from anywhere using your CSE15L account.

## Installing VSCode

Go to https://code.visualstudio.com/ and click the **Download** button for your operating system.

![vscode_image](vscode_download.png)

Opening up VSCode, you should see the terminal at the bottom which is where you will be able to input commands.

![vscode_console](vs_code_terminal.png)

You may also choose to open up PowerShell if that is your preferred command prompt.

## Remotely Connecting

Check if the ssh command is recognized by your system's command prompt.

If not, install the [OpenSSH Client](https://learn.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse?tabs=gui).

![openssh_image](openssh_install.png)

In my case, I already had OpenSSH installed and was able to use the ssh command.

Next, open up the terminal in VS Code or use Windows PowerShell and type in:

> `ssh cs15lfa22zz@ieng6.ucsd.edu`

However, replace the 'zz' characters with your specific CSE15L login which you can find [here](https://sdacs.ucsd.edu/~icc/index.php). When it asks whether you want to continue connecting, type in `yes`.

Enter your password. If it does not work, follow [this tutorial](https://docs.google.com/document/d/1hs7CyQeh-MdUfM9uv99i8tqfneos6Y8bDU0uhn1wqho/edit) to reset it.

Below is a screenshot of what logging in should look like. Notice that the password does not show up as you type it.

![login_image](login_image.png)

## Trying Some Commands

Now that you are remotely logged in, here are a several commands you can run:

- `cd`
- `ls`
- `cp`
- `cat`

`cd` allows you to change your current directory to whatever directory you type in. Putting a tilde instead of an address takes you to your home directory.

`ls` lists out all files in the current directory.

`cp` copies a file or groups of files and takes in two or more parameters

`cat` outputs the contents of the file you type the name of. You can output multiple files by simply appending more file names to the end.

To logout, use the `exit` command.

Here is a screenshot of some of the commands being used on the remote server.

![commands_image](commands.png)

## Moving Files with scp

To exit out of the remote server, use the command `exit`. Now, on your local computer, create a file named `WhereAmI.java` and paste this code inside it.

```
class WhereAmI {
  public static void main(String[] args) {
    System.out.println(System.getProperty("os.name"));
    System.out.println(System.getProperty("user.name"));
    System.out.println(System.getProperty("user.home"));
    System.out.println(System.getProperty("user.dir"));
  }
}
```

Run this code using the `javac` and `java` commands.

To copy this file over to `ieng6`, use the `scp` command, meaning secure copy.

> `scp WhereAmI.java cs15lfa22zz@ieng6.ucsd.edu:~/`

Remember to replace 'zz' with your corresponding login, then type in your password. Note that the passphrase will not appear as you type it. The part after the colon is the path you want to copy the file to. In this case, the file will be copied to the home directory.

Now, this file should appear on the remote server, and you can run the same `javac` and `java` commands there.

If you do all of the above correctly, it should look like this.

![scp_command](scp_command.png)

## Setting an SSH Key

To avoid having to type in our password when logging in or using `scp` every time, we can use `ssh` keys instead. Follow this screenshot to generate your pair of files containing the public and private keys.

![keygen_image](keygen.png)

This should create a folder named `.ssh` which should contain the private and public keys.

![rsa_keys](rsa_keys.png)

Log into the server and create a `.ssh` directory, then return to your client and `scp` the file containing the public key over to the `.ssh` file in the server.

Following these steps will allow you to use `ssh` and `scp` without having to enter your password each time; instead, you will be able to enter your passphrase.

Logging back into your remote server, you may notice that you won't actually see the `.ssh` file appear when you type in the `ls` command. This is because the folder is hidden. To reveal it and all the other hidden files that start with a period, type in `ls -a`.

## Optimizing Remote Running

Here are two shortcuts to remote running that can make the process of running commands and copying files easier.

1. Add a command in double quotes at the end of the ssh command to run a command on the remote server using less steps.

   > `ssh cs15lfa22@ieng6.ucsd.edu "ls"`

   ![run_on_remote](run_on_remote.png)

2. Chain multiple commands together by inserting semi-colons between each command.

   > `cp WhereAmI.java OtherMain.java; javac OtherMain.java; java WhereAmI`

   ![chain_commands](chain_commands.png)
