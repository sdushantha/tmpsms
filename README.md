# tmpsms no longer works

tmpsms was pretty much a wrapper around [Upmasked's](https://upmasked.com/) temporary SMS service but Upmasked seems to have taken down their website as well as their [GitHub account](https://github.com/upmasked/). `tmpsms` may come back in the future if I can find another reliable SMS service. But even if I do find one sometime soon, it unlikely I will further develop `tmpsms` to use that service as I have other priorities.

----

<h1 align="center">
  <img src="images/logo.png">
</h1>

<p align="center">A temporary SMS right from your terminal written in POSIX sh</p>
<p align="center">
<img src="images/demo.gif"> 
</p>

`tmpsms` is a command line utility written in POSIX `sh` that allows you to get a
temporary phone number and receive SMSes. It uses [Upmasked](https://upmasked.com/) temporary SMS service in order to receive the messages. This is a very useful
tool for those testing applications during bug bounty hunting or who just need some privacy and don't want to use a personal phone number.
This is easy to use with simple outputs. `tmpsms` can be integrated with other scripts to improve your workflow.

## Dependencies
- `curl`
- [`jq`](https://github.com/stedolan/jq)
- [`fzf`](https://github.com/junegunn/fzf)

## Installation
```bash
# Download the tmpsms file and make it executable
$ curl -L "https://git.io/tmpsms" > tmpsms && chmod +x tmpsms

# Then move it somewhere in your $PATH. Here is an example:
$ mv tmpsms ~/bin/
```

## Usage
```console
$ tmpsms --help
tmpsms [--count <count>]
tmpsms init [--fzf <arguments>]
tmpsms -h | --version

When called with no options or commands, tmpsms lists
the 3 newest messages.

Options
-h, --help     Show this help message
-c, --count    Only show the <count> newest messages
--version      Show version

Commands
init           Initialize a new phone number by selecting one
               from the available ones using 'fzf'
  --fzf        Extra arguments to use for 'fzf'
```

## Examples
Initialize a new phone number
```console
$ tmpsms init
```

View the 5 newest messages. By default `tmpsms` shows the 3 newest messages.
```console
$ tmpsms --count 5
```

If you find it a hassle to rerun `tmpsms` every few seconds, use `watch` with a delay of 5 seconds. Upmasked only updates messages every 5 seconds.
```console
$ watch -n 5 "tmpsms"
```
