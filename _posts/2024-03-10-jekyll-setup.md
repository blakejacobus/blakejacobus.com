---
layout: post
tags: [work, technology]
---

# Jekyll Setup

## Steps

1. Install [prerequisites](https://jekyllrb.com/docs/installation/)
1. Install [`bundler`](https://jekyllrb.com/docs/installation/ubuntu/)
1. Install [`gems`](https://jekyllrb.com/docs/#instructions)
1. Install [local bootstrap](https://github.com/abhinavs/moonwalk/blob/master/README.md#quick-installation)
1. Start [local server](https://github.com/abhinavs/moonwalk/blob/master/README.md#quick-installation)

## Commands

``` bash
$ sudo apt-get install ruby-full build-essential # ruby install
$ ruby -v
> ruby 3.1.2p20 (2022-04-12 revision 4491bb740a) [x86_64-linux-gnu]
$ gem -v
> 3.3.15
$ make -v
> GNU Make 4.3
$ sudo gem install jekyll bundler
> Successfully installed bundler-2.5.6
# Change to working directory for local theme
$ bin/bootstrap
> Bundle complete! 1 Gemfile dependency, 32 gems now installed.
$ bin/start
> Configuration file: /home/blake/dev/github/blakejacobus.com/_config.yml
>             Source: /home/blake/dev/github/blakejacobus.com
>        Destination: /home/blake/dev/github/blakejacobus.com/_site
>  Incremental build: disabled. Enable with --incremental
>       Generating... 
>        Jekyll Feed: Generating feed for posts
>                     done in 0.256 seconds.
>  Auto-regeneration: enabled for '/home/blake/dev/github/blakejacobus.com'
>     Server address: http://127.0.0.1:4000
>   Server running... press ctrl-c to stop.
```

## Reference

- [Installation](https://jekyllrb.com/docs/installation/)
- [Quickstart](https://jekyllrb.com/docs/#instructions)

### Troubleshooting

Depending on the OS you [install `bundler`](https://jekyllrb.com/docs/installation/) on, you may run into permissions issues when executing the bootstrap script from [Moonwalk](https://github.com/abhinavs/moonwalk/blob/master/README.md#quick-installation):

``` bash
Bundler::PermissionError
There was an error while trying to write to `/var/lib/gems/3.1.0/
It is likely that you need to grant write permissions for that path.
```

- [Fix for `Bundler::PermissionError`](https://github.com/rubygems/rubygems/issues/6272#issuecomment-1381683835)
- [Check permissions in Linux](https://phoenixnap.com/kb/linux-file-permissions)
- [Configure passwordless sudo](https://timonweb.com/devops/how-to-enable-passwordless-sudo-for-a-specific-user-in-linux/)
