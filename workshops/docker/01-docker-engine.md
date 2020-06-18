## Docker Engine

<details><summary>Check if your Docker is up-to-date & running</summary>
<p>

```bash
$ docker info

Client:
 Debug Mode: false

Server:
 Containers: 14
  Running: 0
  Paused: 0
  Stopped: 14
 Images: 24
 Server Version: 19.03.11
 Storage Driver: overlay2
  Backing Filesystem: extfs
  Supports d_type: true
  Native Overlay Diff: true
 Logging Driver: json-file
 Cgroup Driver: cgroupfs
 Plugins:
  Volume: local
  Network: bridge host ipvlan macvlan null overlay
  Log: awslogs fluentd gcplogs gelf journald json-file local logentries splunk syslog
 Swarm: inactive
 Runtimes: runc
 Default Runtime: runc
 Init Binary: docker-init
 containerd version: 7ad184331fa3e55e52b890ea95e65ba581ae3429
 runc version: dc9208a3303feef5b3839f4323d9beb36df0a9dd
 init version: fec3683
 Security Options:
  apparmor
  seccomp
   Profile: default
 Kernel Version: 4.15.0-106-generic
 Operating System: Ubuntu 16.04.6 LTS
 OSType: linux
 Architecture: x86_64
 CPUs: 4
 Total Memory: 11.43GiB
 Name: Lenovo-PB03F4CR
 ID: PRNT:XHQD:ALBB:G3VB:FNAM:NN3H:43VL:KOXW:TKNN:6JVV:SJL2:MMCF
 Docker Root Dir: /var/lib/docker
 Debug Mode: false
 Registry: https://index.docker.io/v1/
 Labels:
 Experimental: false
 Insecure Registries:
  127.0.0.0/8
 Live Restore Enabled: false
```
</p>
</details>

<details><summary>Enter Linux virtual machine</summary>
<p>

```bash
# Windows and Mac
$ docker run -it --rm --privileged --pid=host justincormack/nsenter1

# Mac
$ screen ~/Library/Containers/com.docker.docker/Data/vms/0/tty
```
</p>
</details>


<details><summary>Where is state of the Docker Engine</summary>
<p>

```bash
# Linux & Mac
/var/lib/docker

# Windows
C:\ProgramData\docker
```
</p>
</details>


<details><summary>Check configuration of the Engine</summary>
<p>

```bash
# Linux
/etc/docker/daemon.json

# Windows
C:\ProgramData\docker\config\daemon.json

# Mac
Whale > Preferences > Daemon > Advanced
```
</p>
</details>


<details><summary>Dump Docker Engine communication</summary>
<p>

```bash
$ socat -d -d -t100 \
-lf /dev/stdout \
-v UNIX-LISTEN:/var/run/docker.debug,mode=777,reuseaddr,fork \
UNIX-CONNECT:/var/run/docker.sock

2019/06/27 15:28:23 socat[83151] N listening on LEN=28 AF=1
"/var/run/docker.debug"
2019/06/27 15:28:43 socat[83151] N accepting connection from LEN=16
AF=1 "" on LEN=28 AF=1 "/var/run/docker.debug"
2019/06/27 15:28:43 socat[83161] N opening connection to LEN=22 AF=1
"/var/run/docker.sock"
```
</p>
</details>
