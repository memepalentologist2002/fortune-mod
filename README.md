# fortune-mod Maintenance Version and Ongoing Development

[![Travis-CI Build Status](https://travis-ci.org/shlomif/fortune-mod.svg?branch=master)](https://travis-ci.org/shlomif/fortune-mod)

[![AppVeyor Build status](https://ci.appveyor.com/api/projects/status/0pbvqd1xa7777aoo/branch/master?svg=true)](https://ci.appveyor.com/project/shlomif/fortune-mod/branch/master)

This Git repository maintains the sources for an expurgated version of fortune-mod, a
version of
[the UNIX fortune command](https://en.wikipedia.org/wiki/Fortune_%28Unix%29).
`fortune` is a command-line utility which displays a random quotation from a
collection of quotes. This collection is read from the local [file system](https://en.wikipedia.org/wiki/File_system)
and does not require network access. A large collection of quotes is provided in
the download and installed by default, but more quote collections can be added
by the user. The repo is based on https://github.com/shlomif/fortune-mod

For more information about the original, you can contact
[Shlomi Fish](https://www.shlomifish.org/) .

## Installation

You must compile it from source. (for the time being)

## Release Tarballs

Release tarballs are coming soon.


## Sample usage

```
$ fortune
Enthusiasm is one of the most important
ingredients a volunteer project runs on.
                -- Andreas Schuldei
$
```

## History

I believe fortune-mod was originally forked from the NetBSD version of
fortune, and ported to run on Linux systems. For some time it was maintained
at the currently offline redellipse-dot-net inside a
[GNU Arch](http://en.wikipedia.org/wiki/GNU_arch) (= an old and now mostly
unused version control system) repository, and version 1.99.1 was released as
a tarball.

This maintenance version was initiated by Shlomi Fish, who decided to maintain
it out of being a fan of the fortune command. It started by importing the
unpacked source of the fortune-mod-1.99.1.tar tarball from the Mageia Linux
.src.rpm into an empty git repository and continuing from there.

## What is the difference between fortune-mod and the "normal" fortune?

fortune-mod (= "fortune modified") was the name of a fork of the original
NetBSD fortune, which was done in order to port the code to Linux and apply some
other changes. If you are using a Linux distribution chances are that
the `fortune` executable's package **is** fortune-mod (although in the
case of Debian-and-derivatives it is likely very out-of-date as of September
2020).

## Why is it written in C? Can't it be written in Perl, awk, Python, etc.?

The answer has several parts:

First of all note that according to [the wikipedia page](https://en.wikipedia.org/wiki/Fortune_%28Unix%29)
the original fortune was created in 1979, before the first version of perl was
released in 1987, or python, ruby or Lua which were released later, and when UNIX-running
computers were more underpowered than they are today.

Secondly, you can find some reimplementations of fortune here:

* [perl](https://metacpan.org/pod/distribution/PerlPowerTools/bin/fortune)
* [python](https://github.com/bmc/fortune)

You may be able to get them to work with the data files of fortune-mod and
other fortune collections, but note that I have not closely reviewed their
source codes.

Thirdly, most of the value (and relative data size) of the tarball is in the
quotes collection.

Fourthly, a native executable may still give a [better user experience](https://tonsky.me/blog/disenchantment/)
(I have yet to perform a stresstest benchmark though, and I doubt it will matter too much
for fortune's common use case.)

Finally note that the runtime algorithm is not as straightforward as one may
believe, making use of dat files that contain counts and offsets of the fortune
"cookies".

# What was already done.

1. fortune-mod-1.99.1 was imported into the repository from the Mageia tarball
as the tag <code>fortune-mod-1.99.1</code>.

2. Converted the build system to [CMake](https://en.wikipedia.org/wiki/CMake) .

3. Converted the source files to UTF-8.

4. Added some tests.

5. Removed trailing whitespace.

6. Reformatted long (> 80 chars) lines.

7. Fixed some typos.

8. Added [Travis-CI](https://travis-ci.org/) testing.

9. Added valgrind tests and fixed some memory leaks.

10. Released fortune-mod-1.99.3, fortune-mod-1.99.4, v2.0.0 and up to
version 2.26.0

11. Fixed some C compiler warnings encountered with the GCC compiler flags of
[Shlomif_Common](https://bitbucket.org/shlomif/shlomif-cmake-modules/overview).

12. Added a build-time option to remove the “-o” (= “offensive”) flag, inspired
by a set of patches on the Fedora package.

13. Applied some downstream patches.

14. Fixed as many “clang -Weverything” warnings as possible.

15. lib-recode became maintained again at https://github.com/rrthomas/recode
(thanks to @rrthomas ) thus preventing a switch to something else.

16. Got the build and tests to pass on [AppVeyor/MS Windows](https://ci.appveyor.com/project/shlomif/fortune-mod)
(with some appreciated help).

17. Found and fixed some security issues:
    - Seems to affect some Linux distributions as well as FreeBSD and NetBSD.
        - Was already fixed in OpenBSD
    - https://bugs.mageia.org/show_bug.cgi?id=26567
    - https://advisories.mageia.org/MGASA-2020-0199.html
    - https://bugs.freebsd.org/bugzilla/show_bug.cgi?id=246050
    - https://github.com/shlomif/fortune-mod/commit/fe182a25663261be6e632a2824f6fd653d1d8f45
    - https://github.com/shlomif/fortune-mod/commit/540c495f57e441b745038061a3cfa59e3a97bf33
    - https://github.com/shlomif/fortune-mod/commit/acd338098071bddfa1d21f87e1813727031428ea

18. Reformatted the C code using [clang-format](https://clang.llvm.org/docs/ClangFormat.html).

19. Mostly expurgated the datfiles.
# What remains to be done.

1. See if there are any more downstream patches to apply.

2. Fix more typos (reports and pull-requests are welcome.)

3. Perhaps modernize the code a little.

4. Add more quotes / fortune cookies.

5. Prepare packages for the new releases for [downstream distributions/Operating Systems](https://pkgs.org/download/fortune-mod).

6. Finish expurgating the datfiles.
# Links

* [Shlomi Fish’s Fortune Cookie Files](https://www.shlomifish.org/humour/fortunes/) - on his site, containing links to many other collections of fortune cookies.
* [XML-Grammar-Fortune](https://web-cpan.shlomifish.org/modules/XML-Grammar-Fortune/) - an XML grammar for collections of quotes, allowing one to generate XHTML or plaintext.
* [Anvari.org’s web interface to fortune](http://www.anvari.org/fortune/) - with many collections.

Credit to Shlomi Fish, for the original repo.
