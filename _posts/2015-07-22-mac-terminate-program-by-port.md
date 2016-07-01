---
title: Terminate a program by port on Mac
layout: post
---

Sometimes I need to kill a process. I always have to Google how to do that again. Not anymore. Put this function in `~/.bash_profile`.

```bash
# terminate function
terminate () {
  lsof -i "tcp:$1" | tail -1 | awk '{print $2}' | xargs kill -9 && echo "Killed proces on port $1" || echo "Failed to kill proces on port $1"
}
```

So now you can type `terminate 3000` to kill the process on port `3000`
