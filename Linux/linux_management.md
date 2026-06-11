# Linux Management Lab: Restoring the `student2` User Environment

This exercise involved diagnosing and repairing a broken user environment for `student2`. Although the user account existed, it was missing a home directory and had an unexpected shell configuration.

---

## Objective

Restore a functional login environment for the user `student2` by:

* Creating the missing home directory
* Populating it with default configuration files
* Assigning correct ownership
* Correcting the default shell
* Verifying successful login

---

## 1. Identifying the Problem

Attempting to access the user's home directory revealed that it did not exist.

### Command

```bash
cd /home/student2
```

### Output

```text
-bash: cd: /home/student2: No such file or directory
```

Attempting to switch to the account confirmed the issue.

### Command

```bash
su - student2
```

### Output

```text
su: warning: cannot change directory to /home/student2: No such file or directory
```

### Observation

The user account existed, but its home directory had not been created.

---

## 2. Creating the Home Directory

To restore the user's environment, I created the missing directory.

### Command

```bash
sudo mkdir /home/student2
```

Next, I attempted to copy the default user configuration files from `/etc/skel`.

### Command

```bash
cp -r /etc/skel/. /home/student2
```

### Output

```text
cp: cannot create regular file '/home/student2/./.bash_logout': Permission denied
cp: cannot create regular file '/home/student2/./.bashrc': Permission denied
cp: cannot create regular file '/home/student2/./.profile': Permission denied
```

### Lesson Learned

Creating the directory with `sudo` was not enough. Copying files into it also required elevated privileges.

---

## 3. Populating the Home Directory

I repeated the copy operation with administrative privileges.

### Command

```bash
sudo cp -r /etc/skel/. /home/student2
```

The directory was successfully populated with the default user configuration files.

---

## 4. Fixing Ownership

Because the directory and files were created by `root`, ownership needed to be transferred to `student2`.

### Command

```bash
sudo chown -R student2:student2 /home/student2
```

### Lesson Learned

A user should own their own home directory and its contents. Incorrect ownership can prevent normal file operations.

---

## 5. Encountering an Unexpected Shell

After attempting to log in, I was presented with the Z Shell (`zsh`) setup wizard.

### Output

```text
This is the Z Shell configuration function for new users...
```

### Observation

The account was configured to use `zsh` as its default shell instead of `bash`.

---

## 6. Changing the Default Shell

To match the lab requirements, I changed the default shell to Bash.

### Command

```bash
sudo usermod -s /bin/bash student2
```

I then verified the change.

### Command

```bash
grep student2 /etc/passwd
```

### Output

```text
student2:x:1001:1001::/home/student2:/bin/bash
```

### Lesson Learned

The user's default shell is stored in `/etc/passwd` and can be modified using `usermod -s`.

---

## 7. Verification

After the corrections, I logged in successfully.

### Commands

```bash
su - student2
pwd
```

### Output

```text
/ home/student2
```

I also verified that the default configuration files existed.

### Command

```bash
ls -la
```

### Relevant Output

```text
.bash_logout
.bashrc
.profile
.zcompdump
```

Finally, I tested navigation between directories and confirmed that the `cd` command correctly returned me to the user's home directory.

---

## Results

The `student2` account now has:

* A valid home directory
* Correct file ownership
* Default user configuration files
* Bash configured as the default shell
* A fully functional login environment

---

## Key Takeaways

1. A user account can exist even when its home directory is missing.
2. Default user configuration files are stored in `/etc/skel`.
3. Administrative tasks require appropriate privileges.
4. Ownership should be verified after creating files on behalf of another user.
5. The default shell can be viewed in `/etc/passwd` and modified with `usermod -s`.
6. Troubleshooting often involves following one problem until it reveals the next.


