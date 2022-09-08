# Alien::Build::Plugin::Fetch::HostBlockList ![static](https://github.com/PerlAlien/Alien-Build-Plugin-Fetch-HostBlockList/workflows/static/badge.svg) ![linux](https://github.com/PerlAlien/Alien-Build-Plugin-Fetch-HostBlockList/workflows/linux/badge.svg)

Reject any Alien::Build fetch requests going to hosts in the block list

# SYNOPSIS

Using with environment variables only:

```
export ALIEN_BUILD_PRELOAD=Fetch::HostBlockList
export ALIEN_BUILD_HOST_BLOCK=badsite1.com,badsite2.org
```

Using from `~/.alienbuild/rc.pl`:

```perl
preload_preload 'Fetch::HostBlockList', block_hosts => [qw( badsite1.com badsite2.org )];
```

# DESCRIPTION

This is an [Alien::Build](https://metacpan.org/pod/Alien::Build) plugin that will, when enabled, reject any fetch requests
made by an [Alien::Build](https://metacpan.org/pod/Alien::Build) based [Alien](https://metacpan.org/pod/Alien) that are fetching from a remote host that
is on the block list.

[Alien](https://metacpan.org/pod/Alien)s that bundle packages are not affected, as this plugin does not check
`file` URLs.

If now block list is specified (either via the property or environment variable,
see below), then not hosts will be blocked.

# PROPERTIES

## block\_hosts

```perl
plugin 'Fetch::HostBlockList', block_list => \@hosts;
```

The list of domains that will be blocked.  Should be provided as an array reference.
If not provided, then `ALIEN_BUILD_HOST_BLOCK` will be used (see below).

# ENVIRONMENT

- `ALIEN_BUILD_HOST_BLOCK`

    Comma separated list of hosts to block.  If not specified when the
    plugin is applied then this list will be used.

# SEE ALSO

- [Alien::Build::Plugin::Fetch::HostBlockList](https://metacpan.org/pod/Alien::Build::Plugin::Fetch::HostBlockList)
- [Alien::Build](https://metacpan.org/pod/Alien::Build)
- [alienfile](https://metacpan.org/pod/alienfile)
- [Alien::Build::rc](https://metacpan.org/pod/Alien::Build::rc)

# AUTHOR

Graham Ollis <plicease@cpan.org>

# COPYRIGHT AND LICENSE

This software is copyright (c) 2022 by Graham Ollis.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.
