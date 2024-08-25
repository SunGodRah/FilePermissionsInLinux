# File Permissions in Linux

## Project Description

The research team at my organization needs to modify the file permissions for specific files and directories within the `projects` directory. The current permissions do not align with the intended level of authorization, which could pose a security risk. To safeguard their system, I carried out a series of tasks to review and update these permissions.

## Check File and Directory Details

I used Linux commands to inspect the existing permissions of a particular directory in the file system, as demonstrated in the code below.


<p align="center">
  <img src="https://github.com/user-attachments/assets/e22e888a-655a-49c4-93a0-2584be4953ff" height="60%" width="60%" alt=""/>
</p>

The first line of the screenshot shows the command I entered, while the subsequent lines display the results. This command lists all the contents within the `projects` directory. By using the `ls` command with the `-la` option, I was able to generate a detailed list that includes hidden files. The output reveals one directory named `drafts`, one hidden file called `.project_x.txt`, and five additional project files. The 10-character string in the first column signifies the permissions applied to each file or directory.

## Describe the Permissions String

The 10-character string provides a breakdown of access permissions for each file, indicating who can access it and what they can do. The string is interpreted as follows:

- **1st character:** Either `d` or a hyphen (`-`) signifies the file type. If it’s a `d`, it denotes a directory; if it’s a hyphen (`-`), it indicates a regular file.
- **2nd-4th characters:** These characters show the read (`r`), write (`w`), and execute (`x`) permissions for the user. A hyphen (`-`) in place of one of these characters indicates that the permission is not granted.
- **5th-7th characters:** These characters display the read (`r`), write (`w`), and execute (`x`) permissions for the group. Similarly, a hyphen (`-`) signifies that the permission is not granted.
- **8th-10th characters:** These characters represent the read (`r`), write (`w`), and execute (`x`) permissions for others, which include all users aside from the owner and group. A hyphen (`-`) indicates a lack of permission.

For instance, the permissions for `project_t.txt` are `-rw-rw-r--`. The leading hyphen (`-`) signifies that `project_t.txt` is a file, not a directory. The `r` in the second, fifth, and eighth positions indicates that the user, group, and others have read permissions. The `w` in the third and sixth positions shows that only the user and group have write permissions. No one has execute permissions for `project_t.txt`.

## Change File Permissions

To ensure security, the organization decided that others should not have write access to any files. Based on the permissions I reviewed earlier, I identified that write permissions for others needed to be removed from `project_k.txt`.

The following code illustrates how I executed this change using Linux commands:

<p align="center">
  <img src="https://github.com/user-attachments/assets/f5d5edb9-a786-4b26-b55e-e9a4f86f60cb" height="60%" width="60%" alt=""/>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/0636e53b-a8b6-4ecd-8362-82330ea75e75" height="60%" width="60%" alt=""/>
</p>

The first two lines of the screenshot capture the commands I entered, and the subsequent lines show the output of the second command. The `chmod` command is used to alter permissions on files and directories. The first argument specifies the permission change, and the second argument identifies the target file or directory. In this case, I removed write permissions for others on `project_k.txt`. Afterward, I rechecked the permissions using `ls -la` to confirm the changes.

## Change File Permissions on a Hidden File

The research team recently archived `project_x.txt` and decided that no one should have write access to it, while the user and group should retain read access.

Here’s how I modified the permissions using Linux commands:

<p align="center">
  <img src="https://github.com/user-attachments/assets/eda3f40f-b10b-4ff1-9ce2-8cae26bb3731" height="60%" width="60%" alt=""/>
</p>

The first two lines of the screenshot capture the commands I entered, and the remaining lines show the output of the second command. The `.project_x.txt` file is hidden because it begins with a period (`.`). In this scenario, I removed write permissions from both the user and group and added read permissions for the group. Specifically, I removed write permissions for the user with `u-w`, removed write permissions for the group with `g-w`, and added read permissions for the group with `g+r`.

## Change Directory Permissions

My organization requires that only the `researcher2` user have access to the `drafts` directory and its contents, meaning that no other users should have execute permissions.

The following code demonstrates how I adjusted the permissions accordingly:

<p align="center">
  <img src="https://github.com/user-attachments/assets/df6e1cc2-26a5-450f-b20f-70b30ee128b1" height="60%" width="60%" alt=""/>
</p>
The first two lines of the screenshot capture the commands I entered, and the subsequent lines display the output of the second command. Previously, the group had execute permissions, which I removed using the `chmod` command. The `researcher2` user already had execute permissions, so no further changes were necessary.

## Summary

In summary, I modified several permissions to align with the authorization levels required by my organization for files and directories within the `projects` directory. The first step involved using `ls -la` to verify existing permissions. Based on this information, I then used the `chmod` command to adjust the permissions on various files and directories as needed.




<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
