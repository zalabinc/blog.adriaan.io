---
title: Run cronjobs with dokku PaaS
layout: post
---

I have a crawler running for [watiseropderadio.nl](http://watiseropderadio.nl) and I got some problems with setting up the crontabs for it. I have a node application with a simple node webserver and some other scripts which are runnable via `npm run ...`. I deployed the app to a dokku server and it was running.

Next I wanted to test the `run`-command of dukku:

```sh
ssh -t dokku@xxx.xxx.xxx.xxx -- run crawler npm run npm_script_name --rm
```

It was running fine.

*Note: [Use `--rm` here](https://github.com/progrium/dokku/issues/450#issuecomment-124851555) to not overload your server with not closed docker instances.*

Then I wanted to create a crontab for the crawler, my crontab looked like this:

```sh
# dokku user
* * * * * /usr/local/bin/dokku --rm run crawler npm run npm_script_name
```

but I got errors all the time complaining about a `plugn` `command not found`:

```sh
/var/lib/dokku/plugins/enabled/00_dokku-standard/commands: line 137: plugn: command not found
```

then [I found this GitHub-issue](https://github.com/progrium/dokku/issues/913) and changed my crontab to this and everything worked:

```sh
# dokku user
* * * * * bash -c ': | PATH="$PATH:/usr/local/bin" dokku --rm run crawler npm run npm_script_name'
```

So hopefully someone will not be fighting for a long time with this problem by reading this blog post. Enjoy ;-) 

*Keywords: docker, node, cron*
