##### README

[urldiff](https://github.com/d630/urldiff) is a simple bash shell script to notify and watch changes on websites, that do not provide Atom or RSS-Feed. After reading an url list, downloading and comparision of "local" and "online" a short status report will be generated. The status is constructed like this:

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

Please feel free to open an issue or put in a pull request on https://github.com/D630/urldiff

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
                        ${XDG_DATA_HOME:-${HOME}/.local/share}/urldiff
URLDIFF_MAILTO
                        Default: ${USER}@${HOST}
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

Configure your favourite diff command in the function called `Urldiff::Diff`. To test the connection, modify `Urldiff::CheckConnection` (per default, debian.org will be pinged).

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

urldiff has been written in [GNU bash](http://www.gnu.org/software/bash/) on [Debian GNU/Linux 9 (stretch/sid)](https://www.debian.org) using these programs/packages:

- GNU Awk 4.1.3, API: 1.1 (GNU MPFR 3.1.3-p5, GNU MP 6.1.0)
- GNU Wget 1.17.1
- GNU bash 4.3.42(1)-release
- GNU coreutils 8.23: cp, md5sum, mkdir, mv, rm
- GNU findutils 4.4.2: find, xargs
- Heirloom mailx 12.5
- OpenBSD netcat (Debian patchlevel 1.105-7)
- diffutils 3.3: cmp, diff
- iputils-121221: ping
- ncurses 6.0.20151024: tput
- perl v5.20.2: rename
- sed (GNU sed) 4.2.2
- w3m/0.5.3+git20151119

##### CREDITS

This is an adaption of the [activity-monitor](https://github.com/cmichi/activity-monitor)

##### LICENCE

[Copyrights](../master/doc/COPYRIGHT)
