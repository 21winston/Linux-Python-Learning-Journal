# Daily Log: User Management & System Defaults

## Objective
Mastered Linux user account management, specifically how the system uses background blueprints (`/etc/login.defs`, `/etc/default/useradd`, and `/etc/skel/`) to provision new accounts.

---

## What I Learnt
When you run `useradd`, Linux builds the account using three distinct blueprints:
* **/etc/login.defs**: The global security policy. Dictates password expiration limits and standard UID/GID ranges.
* **/etc/default/useradd**: The command-line fallbacks. Defines things like the default shell if you don't pass specific flags.
* **/etc/skel/**: The skeleton directory. Every file or folder placed here automatically copies into a new user's home directory upon creation.

---

## Hurdles & Lessons Learnt
* **The Overwhelm:** Tried memorizing flags like `-g`, `-u`, and `-m`. Realized it's a waste of brainpower. Using `man` and `--help` locally is the professional way to work.
* **The / Trick:** Navigating huge manual pages sucked until I figured out you can press `/` inside a `man` page to search directly for the exact flag you need. 
* **Tool Failure:** Tried installing `tldr` for quick shortcuts, but hit a corrupted download signature error (`Data.Binary.Get.runGet`). Lesson: Third-party tools break; native tools (`man`) are always reliable.

---
*Pushed via Vim & Git as part of my daily Linux challenge.*
