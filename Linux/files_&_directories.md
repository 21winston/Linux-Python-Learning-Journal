# Linux Files & Directories 

**Timestamps:** access (read), modify (content change), change (metadata change)
- `touch file` → create empty file / update modify time
- `stat file` → view timestamps, inode, permissions

**Inodes:** store metadata (permissions, links, owner, size, timestamps, data pointers) — **not** filename. ext4 = fixed inodes (can run out); XFS = dynamic.

## Links
| | Hard (`ln src dst`) | Soft (`ln -s src dst`) |
|---|---|---|
| Points to | Inode | Filename/path |
| New inode? | No | Yes |
| Cross filesystem? | No | Yes |
| Link directories? | No | Yes |
| Breaks if source deleted? | No | Yes |

- Remove either with `rm` or `unlink`
- `readlink symlink` → shows target

## Directories
- `mkdir dir`, `mkdir -p a/b/c` (nested), `tree` (view structure)

## File Types (`ls -l` 1st char)
`-` file, `l` symlink, `d` dir, `p` pipe, `c` char device, `b` block device, `s` socket
`file <name>` → detects real type via magic number

## Viewing
`cat` (full), `less`/`more` (paged), `head -n N` (top), `tail -n N` (bottom), `tail -f` (live follow)

## Delete / Copy / Move
- `rm file` (`\rm` to skip confirm), `rm -r dir`, `rmdir` (empty dirs only)
- `cp src dst`, `cp -r dirA dirB`, `cp -i` (no overwrite)
- `mv old new` — same FS = rename inode; diff FS = copy+delete
