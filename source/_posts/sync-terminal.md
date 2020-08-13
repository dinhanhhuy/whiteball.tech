---
title: Sycn terminal
---

## Own goal
Sync your command, alias on multiple Mac/Linux devices (event Windows).

``` bash
# Computer 1
$ echo "alias cool=\"echo hello whiteball\"" >> share_profile
$ cool
hello whiteball
$ wsync push

# Computer 2
$ Do you want to update? [Y/N]: Y
Cloning into 'my_profile'...
...
 ___________________________
/ Everything is up to date! \
\ Happy coding...           /
 --------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
$ cool
hello whiteball
```

## TLDR (option 1)
```bash
# PC1
$ curl https://github.com/dinhanhhuy/sync-terminal | sh
...
[INFO]: setup complete, run the following command on other PC
curl whiteball.tech | sh

# PC2
$ curl whiteball.tech | sh
...
[INFO]: sync complete.
```

## Manual setup (option 2)
### PC1
Download wsync binary and move to your default binary folder
```bash
$ wget https://github.com/dinhanhhuy/wsync
$ mv sync /urs/bin/
```
Create a new git repo to storage your alias on [github](https://github.com), [gitlab](https://gitlab.com).
Clone your repo to local PC

``` bash
# etc: cd /home/users/project/share_profile
$ cd [PATH_TO_YOUR_PROJECT]
# etc: git clone https://github.com/whiteball/share_profile .
$ git clone https://github.com/[YOUR_GIT_ACCOUNT]/share_profile . 
$ touch share_profile
```
Write some alias/function to share_profile
```sh
$ echo "alias cls=clear" >> share_profile
$ echo "alias ll='ls -alF'" >> share_profile
```
Connect wsync with your git folder
```sh
# etc: wsync /home/users/project/share_profile
$ wsync [PATH_TO_YOUR_PROJECT]
$ wsync push
```

### PC2

More info: [Server](https://hexo.io/docs/server.html)

### Windows

``` bash
$ hexo deploy
```

## Important note
* This tool DON'T storage your share_profile or git password. You have to re input every time or using `git cache password` for efficient use.

More info: [Deployment](https://hexo.io/docs/one-command-deployment.html)
