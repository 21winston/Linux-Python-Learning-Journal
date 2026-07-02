# Managing Linux Files

## File Structure

A Linux file consists of:

* **Filename** – Human-readable name.
* **Inode** – Stores metadata such as permissions, ownership, timestamps, and pointers to data blocks.
* **Data Blocks** – Store the actual file contents.

A directory is a special file that maps filenames to inode numbers.

### Key Facts

* Filenames are case-sensitive.
* Maximum filename length: **255 characters**.
* Filenames cannot contain `/` or a null character.

---

## Creating Files

Create an empty file:

```bash
touch filea
```

Verify file details:

```bash
stat filea
```

---

## File Timestamps

Linux tracks three main timestamps:

| Timestamp | Purpose                        |
| --------- | ------------------------------ |
| atime     | Last access (read) time        |
| mtime     | Last content modification time |
| ctime     | Last metadata change time      |

View timestamps with:

```bash
stat filename
```

---

## Hard Links

Create a hard link:

```bash
ln source_file.txt hard_link.txt
```

### Important Notes

* Hard links share the same inode.
* Deleting one filename does not delete the data if another hard link exists.
* Data is removed only when the link count reaches **0**.
* Hard links cannot cross filesystems.
* Hard links cannot be created for directories.

---

## Useful Commands

```bash
touch filea          # Create empty file
stat filea           # View file metadata
ln file1 file2       # Create hard link
rm file1             # Remove file
```
