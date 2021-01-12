<h1 align="center">
  <img src="images/logo.png">
</h1>

<p align="center">A temporary SMS right from your terminal written in POSIX sh</p><br>
<p align="center">
<img src="images/demo.gif"> 
</p>

`tmpsms` is a command line utility written in POSIX `sh` that allows you to get a
temporary phone number and receive SMSes. It uses Upmasked temporary SMS service in order to receive the messages. This is a very usefull
tool for those who use are testing applications during bug bounty hunting or just need some privacy and dont wan't to use your personal phone number.

This is a easy to use with simple outputs. `tmpsms` can be intergrated with other scripts to improve your workflow.
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
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
Intilize a new phone number
```console
$ tmpsms init
```

View the 5 newest messages. By default `tmpsms` shows the 3 newest messages.
```console
$ tmpsms --count 5
```

If you find rerunning `tmpsms` every few second to check if your message has arrived a hastle, combine `tmpsms` with `watch`. Use a delay of 5 seconds as Upmasked only get updates the messages every 5 seconds.
```console
$ watch -n 5 "tmpsms"
```
