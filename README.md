### urldiff v0.1.2.0

`urldiff`(1) is a simple bash shell script to notify and watch changes
on websites, that do not provide Atom or RSS-Feed. After reading
an url list, downloading and comparision of "local" and "online"
a little status report will be generated. The status is constructed like this:

```
FAIL 2014-02-12_15:43 URL: $url unattainable
FAIL 2014-02-12_15:43 URL: $url does not match
NEW 2014-02-12_15:43 URL: $url
file://${urldiff}/diff/53e4a875ad5c7ea306cccf991f2768f7_diff.txt
file://${urldiff}/cache/53e4a875ad5c7ea306cccf991f2768f7.html
file://${urldiff}/cache/53e4a875ad5c7ea306cccf991f2768f7.txt
OLD 2014-02-12_15:43 URL: $url
```

This is an adaption of the [activity-monitor](https://github.com/cmichi/activity-monitor)

#### Requirement

Explicitly required:
awk, bash, cmp, cp, diff, find, mailx, md5sum, mkdir, mv, ping, rename, rm, sed, tput, w3m, wget, xargs

Optional: dwdiff, wdiff

#### Options

```
-h, --help
        Display a short help.

-m, --mail [MAILTO...]
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

#### Arguments

```
<MAILTO>
        Something like: user@example.org
```

#### Examples

To print the Report:

```
urldiff
urldiff -nv
```

To only mail the Report:

```
urldiff -q -m
urldiff -q -m user1@example.foo user2@example.foo
```

To do both:

```
urldiff -vb -m
```

#### Notes

- You can write all commands and options without masking `--`. So, instead of `--help` you may use `help`.
- Urls in the url list need to be seperated by newline.
- To check the connection status, google.com will be pinged. If you do not like that, modify it please.

#### Configurations

Set following variables in the third section of the script:

```
urldiffdir=DIR (needed)
urllist=FILE (needed)
mailto=<MAILTO> (optional)
```

Configure your favourite diff-programm in the function called `__urldiff_diff()`.

#### Bugs & Requests

Report it on https://github.com/D630/urldiff
