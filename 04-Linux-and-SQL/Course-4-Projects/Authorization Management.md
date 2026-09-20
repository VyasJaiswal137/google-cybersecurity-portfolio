# Linux File and Directory Permissions Management

## Project Description

In this activity, I managed Linux file and directory permissions for a research organization. The main goal was to follow security policies and apply the principle of least privilege, ensuring that users only had the access they actually needed.

I first inspected the existing permissions using Linux command-line tools. Then, I updated the permissions of regular files, hidden files, and directories to reduce unnecessary access and improve overall security.

## Checking File and Directory Details

To view the contents and existing permissions of the `/home/analyst/projects` directory, I used:

```bash
ls -la
```

The `-l` option displays detailed information such as permissions, ownership, and file properties, while `-a` also shows hidden files.

The directory contained items such as:

- **`drafts/`** — Directory
- **`.project_x.txt`** — Hidden file
- **`project_k.txt`**
- **`project_t.txt`**
- Other project-related documents

The command successfully displayed both regular and hidden files along with their permission details.

## Understanding the Linux Permission String

A Linux permission string contains 10 characters:

```text
-rw-rw-r--
```

These characters can be understood as follows:

| Characters | Meaning |
|---|---|
| 1st | File type: `d` for directory, `-` for regular file |
| 2nd–4th | User/owner permissions |
| 5th–7th | Group permissions |
| 8th–10th | Permissions for other users |

The three permission groups use:

- **`r`** — Read
- **`w`** — Write
- **`x`** — Execute
- **`-`** — Permission is not granted

For example:

```text
-rw-rw-r--
```

This represents a regular file where the owner and group can read and write, while other users can only read the file.

## Changing File Permissions

The security policy required that **Other** users should not have write access to project files.

After checking `project_k.txt`, I found that other users had write permission. I removed it using:

```bash
chmod o-w project_k.txt
```

Here:

- `o` refers to other users.
- `-w` removes write permission.

I then verified the change with:

```bash
ls -l project_k.txt
```

The final permission group for other users showed that write access had been removed.

## Changing Permissions on a Hidden File

The research team had archived `.project_x.txt`. Since the file was archived, it should not be writable. However, both the owner and group still needed read access.

I set the permissions directly using:

```bash
chmod u=r,g=r,o= .project_x.txt
```

This means:

- `u=r` — Owner can read.
- `g=r` — Group can read.
- `o=` — Other users receive no permissions.

I verified the result with:

```bash
ls -la .project_x.txt
```

The resulting permission string reflected the required access restrictions.

## Changing Directory Permissions

The organization also wanted to restrict access to the `drafts` directory. The group had previously been given execute permission on the directory, which was not required under the updated access policy.

I removed the group's execute permission using:

```bash
chmod g-x drafts
```

Here, `g` represents the group and `-x` removes execute permission.

I checked the updated permissions with:

```bash
ls -ld drafts
```

This allowed me to confirm that the group's execute permission had been removed.

## Summary

In this activity, I used Linux commands to inspect and manage file and directory permissions based on security requirements. I used `ls -la` and `ls -ld` to examine permissions and `chmod` to make specific changes.

The activity helped demonstrate how Linux permissions can be used to control access to files and directories and apply the principle of least privilege. By removing unnecessary write and execute permissions, sensitive project data could be better protected from unauthorized access.
