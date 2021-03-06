---
layout: post.html
title: "Part 1: Settings"
tags: [Network]
url: "/~drafts/networks/part-1/"
---

Define our settings for our IRC bot.

### Module setup

If you remember from earlier tutorials, variables that are in all caps are meant to convey that they are constants.  

For our `settings.ini` file, we don’t need to import any special library or package.  We are simply defining the settings that we want our IRC bot to use. [ini files](http://en.wikipedia.org/wiki/INI_file) is just an informal standard for configurations.  If you look at [settings.ini.EXAMPLE](https://github.com/econchick/new-coder/blob/master/network/settings.ini.EXAMPLE), you’ll see two sections: `[irc]` and `[talkback]`. The `[irc]` segment defines the configuration for connecting to an IRC server, while the `[talkback]` section is configuration information specific to our bot.  It’s good to group like-settings and configurations together for easy readability and management.

First, our connection-specific settings:


```
[irc]
endpoint = ssl:host=irc.freenode.net:port=7000
nickName = whatshereallysaid
realName = bot: provides quotations from notable women

channel = #newcoder
```

The `endpoint` identifies which network we want to connect to.  You may remember from the [introduction]( {{ get_url("/networks/intro/")}}) that there are many IRC networks.  You can see that for our bot, we are electing to connect to [Freenode](http://freenode.net).

The `ssl` means we want to connect over [SSL](http://en.wikipedia.org/wiki/Transport_Layer_Security) creating a secure connection.  If we didn’t want an SSL connection, we would replace `ssl` with `tcp`. 

`host` connects to the IRC network we want, in this case: `irc.freenode.net`.  For freenode, the ports to connect to for SSL connections are 6697, 7000, and 7070.  If we were connecting via `tcp` rather than `ssl`, we could select either 6665, 6666, or 6667 (there are some [others](http://freenode.net/irc_servers.shtml), too).  Notice the port depends on type of connection, either SSL or TCP, which is typical of other protocols too (e.g. HTTP listens over 80, while HTTPS listens over 443).

The bot’s `nickName` will show when it’s connected to Freenode, and its `realName` will show when a user queries or requests more information about the bot itself (e.g. with the command, `/whois whatshereallysaid` within a chat window).

Lastly, the `channel` variable, a string that needs to start with `#`. This is the channel that the bot will join when connecting to Freenode.  By default, I have `#newcoder`, which you are welcome to test your IRC bots in when it comes time. 


Next, our bot-specific settings:

```
[talkback]
quotesFile = quotes.txt
# Trigger phrases, in lowercase
triggers =
    that's what she said
```

The `quotesFile` is pretty self-explanatory.  Note that it is in the same directory level as the settings.ini.EXAMPLE file; if you had a different location for the `quotesFile`, you could but in a relative path, `../otherQuotesFile.txt`, or absolute path, `/Users/lynnroot/quotesForBots/otherQuotesFile.txt`.

The `triggers` is the phrase a user says to which the bot will respond.  It could be multiple phrases, but here, we only care about responding when someone says “that‘s what she said”.  If you wanted to add another trigger, just add another line indented by 4 spaces, like so:

```
triggers =
    that's what she said
    that is what she said
    that is what she said!!!
```


All set? Let’s continue with [crafting our quote picker class &rarr;]( {{ get_url("/~drafts/networks/part-2/")}})