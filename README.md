##### README

[urldiff](https://github.com/d630/urldiff) is a simple bash shell script to
notify and watch changes on websites, that do not provide Atom or RSS-Feed.
After reading an url list, downloading and comparision of "local" and "online"
a short status report will be generated. The status is constructed like this:

```
FAIL 2014-02-12_15:43 URL: $url unattainable
FAIL 2014-02-12_15:43 URL: $url does not match
NEW 2014-02-12_15:43 URL: $url
    file://${urldiff}/diff/53e4a875ad5c7ea306cccf991f2768f7_diff.txt
    file://${urldiff}/cache/53e4a875ad5c7ea306cccf991f2768f7.html
    file://${urldiff}/cache/53e4a875ad5c7ea306cccf991f2768f7.txt
OLD 2014-02-12_15:43 URL: $url
```

Urls in the url list need to be seperated by newline.

##### BUGS & REQUESTS

Please feel free to open an issue or put in a pull request on
https://github.com/D630/urldiff

##### GIT

To download the very latest source code:

```
git clone https://github.com/D630/urldiff
```

In order to use the latest tagged version, do also something like this:

```
cd -- ./urldiff
git checkout $(git describe --abbrev=0 --tags)
```

##### INSTALL

Just put `./bin/urldiff` on your PATH.

##### USAGE

###### INVOCATION

```sh
urldiff [ -h | -v ] [ -nv | -nv | -q ] [ -m ]
```

###### ENVIRONMENT VARIABLES

```
URLDIFF_DATA
                        Default:
                        ${XDG_DATA_HOME:-$HOME/.local/share}/urldiff
URLDIFF_MAILTO
                        Default: $USER@$HOST
```

###### OPTIONS

```
-h, --help
        Display a short help.

-m, --mail [ MAILTO... ]
        Send Report via mail to <MAILTO>. If <MAILTO> is not specified,
        the configuration variable <mailto> will be used.

-nv, --no-verbose
        Turn off verbose output without being completely quiet.

-q, --quiet
        Turn off output.

-vb, --verbose
        Turn on verbose output. By default, this option is used.

-v, --version
        Print current version of urldiff(1).
```

###### ARGUMENTS

```
<MAILTO>
        Something like: foo@bar.org
```

###### CONFIGURATIONS

Configure your favourite diff command in the function called `Urldiff::Diff`.
To test the connection, modify `Urldiff::CheckConnection` (per default,
debian.org will be pinged).

###### EXAMPLES

To print the report:

```
urldiff
urldiff -nv
```

Only mail the report with:

```
urldiff -q -m
urldiff -q -m user1@example.foo user2@example.foo
```

To do both:

```
urldiff -vb -m
```

##### NOTICE

urldiff has been written in [GNU bash](http://www.gnu.org/software/bash/) on
[Debian GNU/Linux stretch/sid (4.9.6-3 x86-64)](https://www.debian.org) using
the following programs/packages:

- GNU Awk 4.1.4, API: 1.1 (GNU MPFR 3.1.5, GNU MP 6.1.2)
- GNU Wget 1.18
- GNU bash 4.4.11(1)-release
- GNU coreutils 8.26: cat, cp, md5sum, mkdir, mv, rm
- GNU diffutils 3.5: cmp, diff
- GNU ed 1.10
- GNU findutils 4.7.0-git: find, xargs
- OpenBSD netcat (Debian patchlevel 1.130-2)
- bsd-mailx (8.1.2-0.20160123cvs-3)
- iputils-s20161105: ping
- ncurses 6.0.20161126: tput
- perl v5.20.2: File::Rename (0.20)
- w3m/0.5.3+git20170102

##### CREDITS

This is an adaption of the [activity-monitor](https://github.com/cmichi/activity-monitor)

##### LICENCE

[Copyrights](../master/doc/COPYRIGHT)
