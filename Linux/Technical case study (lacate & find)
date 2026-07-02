Linux Learning Journal -- `updatedb`, `locate`, `find`, and Verifying Documentation
Original Project Goal
I initially wanted to audit a "broken" `/etc/updatedb.conf` to
understand how `updatedb`, `locate`, and `find` differed, especially
around privacy lockouts and indexing.
I framed the project around three observations:
A commented `PRUNENAMES` line (`#`) has no effect because it is
ignored.
Deleting `PRUNENAMES` doesn't make indexing stricter; it removes
that pruning rule.
Adding `.old` to `PRUNENAMES` still allowed `locate` to find
`backdoor.old`.
At first this looked like a configuration failure.
What Actually Happened
The investigation showed the configuration was working.
The incorrect assumption was that:
``` text
PRUNENAMES=".old"
```
would match every filename ending in `.old`.
It doesn't.
`PRUNENAMES` performs literal basename matching.
Examples:
`.git` ✅ matches
`.old` ✅ matches
`backdoor.old` ❌ does not match
`staged.old` ❌ does not match
This completely changed my understanding of how `updatedb` works.
Bigger Lesson
The project itself became outdated because it assumed Linux was
malfunctioning.
Instead, Linux behaved correctly and revealed that my mental model was
wrong.
The real project became learning how to debug assumptions.
Difference Between locate and find
`locate` - Searches a pre-built database. - Depends on `updatedb`. - Can
only find what has been indexed.
`find` - Walks the filesystem live. - Ignores the locate database. -
Always reflects the current filesystem.
Understanding updatedb.conf
`updatedb.conf` only controls what is indexed.
Editing it does not - delete files, - rename files, - hide files
from `find`.
It only changes what appears in the next `locate` database after running
`updatedb`.
Another Documentation Issue
The book correctly introduced `find -exec` but its explanation stated
that `{}` represents the output of `find` becoming the standard input of
the executed command.
A more accurate explanation is:
`{}` is replaced with the pathname of each matching file.
That pathname is passed as a command-line argument.
It is not passed through standard input (stdin).
Conceptually:
``` bash
find /var/log -name "*.log" -exec ls -l {} \;
```
becomes
``` bash
ls -l /var/log/auth.log
ls -l /var/log/syslog.log
```
not a pipeline.
Reflection
The biggest lesson wasn't about `updatedb`.
It was about verification.
When experiments contradicted the documentation, I kept investigating
instead of assuming the operating system was wrong.
That process taught me to: - validate documentation with experiments, -
distinguish observed behavior from assumptions, - consult system
behavior (`man` pages and testing) over memorization, - build accurate
mental models instead of collecting commands.
Today's work transformed a simple Linux exercise into a lesson in
systems thinking and debugging.
