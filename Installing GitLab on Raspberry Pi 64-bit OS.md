## Getting Started[](https://about.gitlab.com/blog/2022/03/14/installing-gitlab-on-raspberry-pi-64-bit-os/#getting-started)

The typical [install for GitLab on the Raspberry Pi](https://about.gitlab.com/install/#raspberry-pi-os) assumes you have the standard 32-bit version of `raspbian/buster` that has been standard for some time. So following those steps, I ran into an error with the install script.

When running

```
sudo curl -sS https://packages.gitlab.com/install/repositories/gitlab/raspberry-pi2/script.deb.sh | sudo bash
```

It appeared to work, but if I tried to install GitLab I'd get this error

```
$ sudo EXTERNAL_URL="https://gitpi.boleary.dev" apt-get install gitlab-ce

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package gitlab-ce is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
 
E: Package 'gitlab-ce' has no installation candidate
```

That's related to the fact that specifically this version of Raspberry Pi OS isn't supported yet - but since it is a fork of Debian Linux, I was able to work around that.

## Manual Installation[](https://about.gitlab.com/blog/2022/03/14/installing-gitlab-on-raspberry-pi-64-bit-os/#manual-installation)

To get started with a slightly modified installation path, I first got the package details and appropriate prerequisite libraries installed:

```
curl -s https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | sudo bash

sudo apt-get update

sudo apt-get install debian-archive-keyring

sudo apt-get install curl gnupg apt-transport-https

curl -L https://packages.gitlab.com/gitlab/gitlab-ce/gpgkey | sudo apt-key add -
```

Then I created a new sources list to point `apt` to for the installation with `sudo touch /etc/apt/sources.list.d/gitlab_gitlab-ce.list`

Next, I manually added the Debian Buster repositories to that sources list I just created by modifying `/etc/apt/sources.list.d/gitlab_gitlab-ce.list` to add:

```
deb https://packages.gitlab.com/gitlab/gitlab-ce/debian/ buster main
deb-src https://packages.gitlab.com/gitlab/gitlab-ce/debian/ buster main
```

## Finishing Up[](https://about.gitlab.com/blog/2022/03/14/installing-gitlab-on-raspberry-pi-64-bit-os/#finishing-up)

From there, it was easy to install the 'standard' way, with apt-get handling the rest for me.

```
sudo apt-get update

sudo EXTERNAL_URL="http://gitpi.boleary.dev" apt-get install gitlab-ce
```

## Next Steps[](https://about.gitlab.com/blog/2022/03/14/installing-gitlab-on-raspberry-pi-64-bit-os/#next-steps)

Now, those who love DNS will notice that I was pointing to a fully qualified domain name, but it points to a private address if you look up that address.

```
dig gitpi.boleary.dev
; <<>> DiG 9.10.6 <<>> gitpi.boleary.dev
;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;gitpi.boleary.dev.		IN	A

;; ANSWER SECTION:
gitpi.boleary.dev.	300	IN	A	100.64.205.40
```

Isn't that interesting? What does it mean - can I access it from outside my house's network? And how will I get it to work with HTTPs on that private address?

For those answers, you'll have to stay tuned to my next article about running GitLab on the Raspberry Pi: Hosting a private GitLab server with Tailscale and LetsEncrypt.