---
title: macOS Sierra Broke My Git
---

One morning I was running `git status`. I got this ugly error message in my terminal:

```bash
xcrun: error: invalid active developer path (/Library/Developer/CommandLineTools), missing xcrun at: /Library/Developer/CommandLineTools/usr/bin/xcrun
```

This is of course not very workable. I installed macOS Sierra last night. After reading some [post](https://ohthehugemanatee.org/blog/2015/10/01/how-i-got-el-capitain-working-with-my-developer-tools/)s on disableing System Integrity Protection I found a [StackOverflow issue](http://stackoverflow.com/questions/32925000/git-doesnt-work-after-upgrading-mac-os-x-el-capitain) on this subject. It didn't need to disable any System Integrity Protection, just one simple command:

```bash
xcode-select --install
```

Git was working again. Unfortunatly Homebrew still had issues like 

```
Error: /usr/local is not writable. You should change the ownership
and permissions of /usr/local back to your user account:
  sudo chown -R $(whoami) /usr/local
```

but just do what Homebrew says and you're done!
