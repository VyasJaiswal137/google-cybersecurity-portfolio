# Lab: Decrypting Files in Linux

---

## Scenario Overview

In this lab, every file in the home directory has been encrypted. The task is to use basic Linux Bash commands to break a Caesar cipher, decrypt the files, and read the hidden messages inside. The session begins logged in as the user **analyst**, with `/home/analyst` as the current working directory.

The work follows three stages: exploring the home directory and reading a file, locating a hidden file and solving the Caesar cipher it contains, and finally decrypting the encrypted data file to recover the data and reveal the hidden message.

---

## Task 1: Read the Contents of a File

The lab starts in the home directory, `/home/analyst`. The first step is to list the directory contents to see what is present.

```bash
ls /home/analyst
```

Output:

```text
Q1.encrypted  README.txt  caesar
```

Two files and one subdirectory are present. The `README.txt` file holds the instructions needed to proceed, and it can be read with the `cat` command.

```bash
cat README.txt
```

Output:

```text
Hello,
All of your data has been encrypted. To recover your data, you will need to solve a cipher. To get started look for a hidden file in the caesar subdirectory.
```

The message directs attention to the `caesar` subdirectory, which contains a hidden file holding further instructions.

---

## Task 2: Find a Hidden File

The next step is to move into the `caesar` subdirectory and locate the hidden file.

```bash
cd caesar
```

Because hidden files in Linux begin with a period (`.`), a standard listing will not show them. The `-a` option is required to display all files.

```bash
ls -a
```

Output:

```text
.  ..  .leftShift3
```

The hidden file is named `.leftShift3`. Reading it with `cat` reveals scrambled text, which indicates a Caesar cipher. The cipher works by shifting each alphabet character a fixed number of positions — in this case, three letters to the left, so `d` stands for `a` and `e` stands for `b`.

```bash
cat .leftShift3
```

The scrambled content can be decrypted using the `tr` command, which translates text from one set of characters to another using a mapping. The first parameter represents the input set and the second represents the output set.

```bash
cat .leftShift3 | tr "d-za-cD-ZA-C" "a-zA-Z"
```

Output:

```text
In order to recover your files you will need to enter the following command:

openssl aes-256-cbc -pbkdf2 -a -d -in Q1.encrypted -out Q1.recovered -k ettubrute
```

In this mapping, the character set `d-za-cD-ZA-C` is translated back to `a-zA-Z`, restoring every letter to its original position. The output supplies the command needed for the final task. Before continuing, the analyst returns to the home directory.

```bash
cd ~
```

---

## Task 3: Decrypt a File

With the Caesar cipher solved, the command revealed in `.leftShift3` is used to decrypt the encrypted file and recover the data.

```bash
openssl aes-256-cbc -pbkdf2 -a -d -in Q1.encrypted -out Q1.recovered -k ettubrute
```

The syntax breaks down as follows:

| Option | Purpose |
| --- | --- |
| `openssl` | Reverses the encryption of the file using a secure symmetric cipher. |
| `aes-256-cbc` | Specifies the cipher used. |
| `-pbkdf2` | Adds extra security to the key. |
| `-a` | Indicates the desired encoding for the output. |
| `-d` | Indicates decryption. |
| `-in` | Specifies the input file. |
| `-out` | Specifies the output file. |
| `-k` | Specifies the password, which in this example is `ettubrute`. |

Listing the directory again confirms that the new `Q1.recovered` file has been created.

```bash
ls
```

The decrypted file can then be read to reveal its message.

```bash
cat Q1.recovered
```

---

## Conclusion

This lab provided practical experience with basic Linux Bash shell commands for listing hidden files, decrypting a Caesar cipher, and decrypting an encrypted file. It serves as an important milestone toward understanding encryption and decryption.