---
layout: post
---

A cool new service from The Netherlands is launched. It is called [https://transfer.sh](https://transfer.sh/?rel=blog.adriaan.io). With a simple command from the terminal you can send a file to their server. You will get a short url back and you can share it because it is online available.

```bash
curl --upload-file ./hello.txt https://transfer.sh/hello.txt 
```

It will return you the url where it is hosted, for example `https://transfer.sh/66nb8/hello.txt`.

If you don't like to type this every time you can copy the following script and put that in your `.bash_profile`, `.bashrc` or `.zshrc`.

```bash
# function for transfer.sh
transfer() {
  if [ $# -eq 0 ]; then echo "No arguments specified. Usage:\necho transfer /tmp/test.md\ncat /tmp/test.md | transfer test.md"; return 1; fi
  tmpfile=$( mktemp -t transferXXX ); if tty -s; then basefile=$(basename "$1" | sed -e 's/[^a-zA-Z0-9._-]/-/g'); curl --progress-bar --upload-file "$1" "https://transfer.sh/$basefile" >> $tmpfile; else curl --progress-bar --upload-file "-" "https://transfer.sh/$1" >> $tmpfile ; fi; cat $tmpfile; rm -f $tmpfile;
}
```

There are a lot of more options how to use the service, see [https://transfer.sh](https://transfer.sh/?rel=blog.adriaan.io).
