## Docker Container

<details><summary>1. Download a test image and run it</summary>
<p>

```bash
$ docker run hello-world
Hello from Docker!
This message shows that your installation appears to be
working correctly.
```
</p>
</details>


<details><summary>2. Download a sandbox image and run a command inside</summary>
<p>

```bash
$ docker run busybox echo Hello World
Hello World
```
</p>
</details>


<details><summary>3. Download a base image and attach to it interactively</summary>
<p>

```bash
$ docker run -it debian:stretch
root@machine:/# cat /etc/os-release
PRETTY_NAME="Debian GNU/Linux 9 (stretch)"
NAME="Debian GNU/Linux"
VERSION_ID="9"
VERSION="9 (stretch)"
```
</p>
</details>


<details><summary>4.1. Download a minimalist base image and attach to it interactively ...</summary>
<p>

```bash
$ docker run -it alpine:3.9
/ # apk info
##
musl
busybox
alpine-baselayout
alpine-keys
libcrypto1.1
libssl1.1
ca-certificates-cacert
```
</p>
</details>


<details><summary>4.2. ... install a package inside...</summary>
<p>

```bash
/ # apk update
...
OK: 9766 distinct packages available
/ # apk add figlet
(1/1) Installing figlet (2.2.5-r0)
Executing busybox-1.29.3-r10.trigger
OK: 6 MiB in 15 packages
```
</p>
</details>


<details><summary>4.3. ... use it...</summary>
<p>

```bash
/ # figlet Docker
```
</p>
</details>
