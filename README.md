# curly
*Error checking curl wrapper*

This is the curl wrapper I end up writing for every second shell script.
I wish this was built into curl, but it [doesn't look like it will
happen](https://twitter.com/discordianfish/status/854727950075392000).

It's basically `curl -f` but still printing the document:

- Always retrieve/print the document
- Return with exit code 121 if http status is >=400 or <200

Internally it uses the `-w` and `-o` flags, so you can't use them when using the
wrapper.

**Example:**

```
$ ./curly -s httpstat.us/502; echo " status: $?"
502 Bad Gateway status: 121
```
