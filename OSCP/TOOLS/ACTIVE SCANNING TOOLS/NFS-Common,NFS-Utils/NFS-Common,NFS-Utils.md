# Packages and Binaries:

### libnfsidmap-dev

Contains the header files and documentation for libnfsidmap for use in developing applications that use the libnfsidmap library.

libnfsidmap provides functions to map between NFSv4 names (which are of the form user@domain) and local uid’s and gid’s.

**Installed size:** `110 KB`  
**How to install:** `sudo apt install libnfsidmap-dev`

Dependencies:

- libnfsidmap1

---

### libnfsidmap1

libnfsidmap provides functions to map between NFSv4 names (which are of the form user@domain) and local uid’s and gid’s.

**Installed size:** `277 KB`  
**How to install:** `sudo apt install libnfsidmap1`

Dependencies:

- libc6
- libldap-2.5-0

---

### nfs-common

Use this package on any machine that uses NFS, either as client or server. Programs included: lockd, statd, showmount, nfsstat, gssd, idmapd and mount.nfs.

**Installed size:** `1.09 MB`  
**How to install:** `sudo apt install nfs-common`

Dependencies:

- adduser
- init-system-helpers
- keyutils
- libc6
- libcap2
- libcom-err2
- libdevmapper1.02.1
- libevent-core-2.1-7t64
- libgssapi-krb5-2
- libkeyutils1
- libkrb5-3
- libmount1
- libnfsidmap1
- libtirpc3t64
- libwrap0
- python3
- rpcbind
- ucf

##### blkmapd

PNFS block layout mapping daemon

```console
root@kali:~# blkmapd -h
Usage: blkmapd [-hdf]
```

---

##### mount.nfs

Mount a Network File System

```console
root@kali:~# mount.nfs -h
usage: mount.nfs remotetarget dir [-rvVwfnsh] [-o nfsoptions]
options:
	-r		Mount file system readonly
	-v		Verbose
	-V		Print version
	-w		Mount file system read-write
	-f		Fake mount, do not actually mount
	-n		Do not update /etc/mtab
	-s		Tolerate sloppy mount options rather than fail
	-h		Print this help
	nfsoptions	Refer to mount.nfs(8) or nfs(5)

```

---

##### mount.nfs4

Mount.nfs (8) - mount a Network File System

```console
root@kali:~# mount.nfs4 -h
usage: mount.nfs4 remotetarget dir [-rvVwfnsh] [-o nfsoptions]
options:
	-r		Mount file system readonly
	-v		Verbose
	-V		Print version
	-w		Mount file system read-write
	-f		Fake mount, do not actually mount
	-n		Do not update /etc/mtab
	-s		Tolerate sloppy mount options rather than fail
	-h		Print this help
	nfsoptions	Refer to mount.nfs(8) or nfs(5)

```

---

##### mountstats

Displays various NFS client per-mount statistics

```console
root@kali:~# mountstats -h
usage: mountstats [-h] {mountstats,nfsstat,iostat} ...

positional arguments:
  {mountstats,nfsstat,iostat}
                        sub-command help
    mountstats          Display a combination of per-op RPC statistics, NFS
                        event counts, and NFS byte counts. This is the default
                        sub-command if no sub-command is given.
    nfsstat             Display nfsstat-like statistics.
    iostat              Display iostat-like statistics.

options:
  -h, --help            show this help message and exit

For specific sub-command help, run 'mountstats SUB-COMMAND -h|--help'
```

---

##### nfsconf

Query various NFS configuration settings

```console
root@kali:~# nfsconf -h
nfsconf: invalid option -- 'h'
Usage: nfsconf [-v] [--file filename.conf] ...
Options:
 -v			Increase Verbosity
 --file filename.conf	Load this config file
     (Default config file: /etc/nfs.conf
 --modified "info"	Use "info" in file modified header
Modes:
  --dump [outputfile]
      Outputs the configuration to the named file
  --get [--arg subsection] {section} {tag}
      Output one specific config value
  --entry [--arg subsection] {section} {tag}
      Output the uninterpreted config entry
  --isset [--arg subsection] {section} {tag}
      Return code indicates if config value is present
  --set [--arg subsection] {section} {tag} {value}
      Set and Write a config value
  --unset [--arg subsection] {section} {tag}
      Remove an existing config value
```

---

##### nfsidmap

The NFS idmapper upcall program

```console
root@kali:~# nfsidmap -h
nfsidmap: Usage: nfsidmap [-vh] [-c || [-u|-g|-r key] || -d || -l || [-t timeout] key desc]
```

---

##### nfsiostat

Emulate iostat for NFS mount points using /proc/self/mountstats

```console
root@kali:~# nfsiostat -h
Usage: nfsiostat [ <interval> [ <count> ] ] [ <options> ] [ <mount point> ]

 Sample iostat-like program to display NFS client per-mount' statistics.  The
<interval> parameter specifies the amount of time in seconds between each
report.  The first report contains statistics for the time since each file
system was mounted.  Each subsequent report contains statistics collected
during the interval since the previous report.  If the <count> parameter is
specified, the value of <count> determines the number of reports generated at
<interval> seconds apart.  If the interval parameter is specified without the
<count> parameter, the command generates reports continuously. If one or more
<mount point> names are specified, statistics for only these mount points will
be displayed.  Otherwise, all NFS mount points on the client are listed.

Options:
  --version             show program's version number and exit
  -h, --help            show this help message and exit

  Statistics Options:
    File I/O is displayed unless one of the following is specified:

    -a, --attr          displays statistics related to the attribute cache
    -d, --dir           displays statistics related to directory operations
    -p, --page          displays statistics related to the page cache

  Display Options:
    Options affecting display format:

    -s, --sort          Sort NFS mount points by ops/second
    -l LIST, --list=LIST
                        only print stats for first LIST mount points
```

---

##### nfsstat

List NFS statistics

```console
root@kali:~# nfsstat --help
Usage: nfsstat [OPTION]...

  -m, --mounts		Show statistics on mounted NFS filesystems
  -c, --client		Show NFS client statistics
  -s, --server		Show NFS server statistics
  -2			Show NFS version 2 statistics
  -3			Show NFS version 3 statistics
  -4			Show NFS version 4 statistics
  -o [facility]		Show statistics on particular facilities.
     nfs		NFS protocol information
     rpc		General RPC information
     net		Network layer statistics
     fh			Usage information on the server's file handle cache
     io			Usage information on the server's io statistics
     ra			Usage information on the server's read ahead cache
     rc			Usage information on the server's request reply cache
     all		Select all of the above
  -v, --verbose, --all	Same as '-o all'
  -r, --rpc		Show RPC statistics
  -n, --nfs		Show NFS statistics
  -Z[#], --sleep[=#]	Collects stats until interrupted.
			    Cumulative stats are then printed
          		    If # is provided, stats will be output every
			    # seconds.
  -S, --since file	Shows difference between current stats and those in 'file'
  -l, --list		Prints stats in list format
  --version		Show program version
  --help		What you just did

```

---

##### rpc.gssd

RPCSEC_GSS daemon

```console
root@kali:~# rpc.gssd -h
rpc.gssd: invalid option -- 'h'
usage: rpc.gssd [-f] [-l] [-M] [-n] [-v] [-r] [-p pipefsdir] [-k keytab] [-d ccachedir] [-t timeout] [-R preferred realm] [-D] [-H] [-U upcall timeout] [-C]
```

---

##### rpc.idmapd

NFSv4 ID <-> Name Mapper

```console
root@kali:~# rpc.idmapd -h
Usage: rpc.idmapd [-hfvCS] [-p path] [-c path]
```

---

##### rpc.statd

NSM service daemon

```console
root@kali:~# rpc.statd -h
usage: rpc.statd [options]
      -h, -?, --help       Print this help screen.
      -F, --foreground     Foreground (no-daemon mode)
      -d, --no-syslog      Verbose logging to stderr.  Foreground mode only.
      -p, --port           Port to listen on
      -o, --outgoing-port  Port for outgoing connections
      -V, -v, --version    Display version information and exit.
      -n, --name           Specify a local hostname.
      -P                   State directory path.
      -N                   Run in notify only mode.
      -L, --no-notify      Do not perform any notification.
      -H                   Specify a high-availability callout program.
```

---

##### rpc.svcgssd

Server-side rpcsec_gss daemon

```console
root@kali:~# rpc.svcgssd -h
rpc.svcgssd: invalid option -- 'h'
usage: rpc.svcgssd [-n] [-f] [-v] [-r] [-i] [-p principal]
```

---

##### rpcctl

Displays SunRPC connection information

```console
root@kali:~# rpcctl -h
usage: rpcctl [-h] {client,switch,xprt} ...

options:
  -h, --help            show this help message and exit

commands:
  {client,switch,xprt}
    client              Commands for rpc clients
    switch              Commands for xprt switches
    xprt                Commands for individual xprts
```

---

##### rpcdebug

Set and clear NFS and RPC kernel debug flags

```console
root@kali:~# rpcdebug -h
usage: rpcdebug [-v] [-h] [-m module] [-s flags...|-c flags...]
       set or cancel debug flags.
       (use rpcdebug -vh to get a list of modules and valid flags)
```

---

##### showmount

Show mount information for an NFS server

```console
root@kali:~# showmount -h
Usage: showmount [-adehv]
       [--all] [--directories] [--exports]
       [--no-headers] [--help] [--version] [host]
```

---

##### sm-notify

Send reboot notifications to NFS peers

```console
root@kali:~# sm-notify -h
sm-notify: invalid option -- 'h'
Usage: sm-notify -notify [-dfq] [-m max-retry-minutes] [-p srcport]
            [-P /path/to/state/directory] [-v my_host_name]
```

---

##### start-statd

---

##### umount.nfs

Unmount a Network File System

```console
root@kali:~# umount.nfs -h
usage: umount.nfs dir [-fvnrlh]
options:
	-f	force unmount
	-v	verbose
	-n	Do not update /etc/mtab
	-r	remount
	-l	lazy unmount
	-h	print this help

```

---

##### umount.nfs4

Umount.nfs (8) - unmount a Network File System

```console
root@kali:~# umount.nfs4 -h
usage: umount.nfs4 dir [-fvnrlh]
options:
	-f	force unmount
	-v	verbose
	-n	Do not update /etc/mtab
	-r	remount
	-l	lazy unmount
	-h	print this help

```

---

### nfs-kernel-server

The NFS kernel server is currently the recommended NFS server for use with Linux, featuring features such as NFSv3 and NFSv4, Kerberos support via GSS, and much more. It is also significantly faster and usually more reliable than the user-space NFS servers (from the unfs3 and nfs-user-server packages). However, it is more difficult to debug than the user-space servers, and has a slightly different feature set.

This package contains the user-space support needed to use the NFS kernel server. Most administrators wishing to set up an NFS server would want to install this package.

**Installed size:** `773 KB`  
**How to install:** `sudo apt install nfs-kernel-server`

Dependencies:

- keyutils
- libblkid1
- libc6
- libcap2
- libevent-core-2.1-7t64
- libsqlite3-0
- libtirpc3t64
- libuuid1
- libwrap0
- libxml2
- netbase
- nfs-common
- ucf

##### exportfs

Maintain table of exported NFS file systems

```console
root@kali:~# exportfs -h
usage: exportfs [-adfhioruvs] [host:/path]
```

---

##### fsidd

---

##### nfsdcld

NFSv4 Client Tracking Daemon

```console
root@kali:~# nfsdcld -h
nfsdcld [ -hFd ] [ -p pipefsdir ] [ -s storagedir ]
```

---

##### nfsdclddb

Tool for manipulating the nfsdcld sqlite database

```console
root@kali:~# nfsdclddb -h
usage: nfsdclddb [-h] [-p PATH] {fix-table-names,downgrade-schema,print} ...

positional arguments:
  {fix-table-names,downgrade-schema,print}
                        sub-command help
    fix-table-names     fix invalid table names
    downgrade-schema    downgrade database schema
    print               print database info

options:
  -h, --help            show this help message and exit
  -p PATH, --path PATH  path to the database (default:
                        /var/lib/nfs/nfsdcld/main.sqlite)
```

---

##### nfsdclnts

Print various nfs client information for knfsd server.

```console
root@kali:~# nfsdclnts -h
usage: nfsdclnts [-h] [-t type] [--clientinfo] [--hostname] [-v] [-f  [...]]
                 [-q]

Parse the nfsd states and clientinfo files.

options:
  -h, --help            show this help message and exit
  -t type, --type type  Input the type that you want to be printed: open,
                        lock, deleg, layout, all
  --clientinfo          output clients information, --hostname is implied.
  --hostname            print hostname of client instead of its ip address.
                        Longer hostnames are truncated.
  -v, --verbose         Verbose operation, show debug messages.
  -f  [ ...], --file  [ ...]
                        pass client states file, provided that info file
                        resides in the same directory.
  -q, --quiet           don't print the header information
```

---

##### nfsdcltrack

NFSv4 Client Tracking Callout Program

```console
root@kali:~# nfsdcltrack -h
Usage: nfsdcltrack [ -hfd ] [ -s dir ] < cmd > < arg >
Where < cmd > is one of the following and takes the following < arg >:
    init
    create <nfs_client_id4>
    remove <nfs_client_id4>
    check  <nfs_client_id4>
    gracedone <epoch time>
```

---

##### nfsref

Manage NFS referrals

```console
root@kali:~# nfsref -h
nfsref: invalid option -- 'h'
Usage: nfsref [ -t type ] SUBCOMMAND [ ARGUMENTS ]

SUBCOMMAND is one of:
	add        Add a new junction
	remove     Remove an existing junction
	lookup     Enumerate a junction

Use "nfsref SUBCOMMAND -?" for details.
```

---

##### rpc.mountd

NFS mount daemon

```console
root@kali:~# rpc.mountd -h
Usage: rpc.mountd [-F|--foreground] [-h|--help] [-v|--version] [-d kind|--debug kind]
	[-l|--log-auth] [-i|--cache-use-ipaddr] [-T|--ttl ttl]
	[-o num|--descriptors num]
	[-p|--port port] [-V version|--nfs-version version]
	[-N version|--no-nfs-version version] [-n|--no-tcp]
	[-H prog |--ha-callout prog] [-r |--reverse-lookup]
	[-s|--state-directory-path path] [-g|--manage-gids]
	[-t num|--num-threads=num] [-u|--no-udp]
```

---

##### rpc.nfsd

NFS server process

```console
root@kali:~# rpc.nfsd -h
Usage:
rpc.nfsd [-d|--debug] [-H hostname] [-p|-P|--port port]
   [-N|--no-nfs-version version] [-V|--nfs-version version]
   [-s|--syslog] [-t|--tcp] [-T|--no-tcp] [-u|--udp] [-U|--no-udp]
   [-r|--rdma=] [-G|--grace-time secs] [-L|--leasetime secs] nrservs
```

---

Updated on: 2024-Aug-06

**Credit:** This information was adapted from an excellent guide on [Kali.org](https://www.kali.org/tools/nfs-utils/). Be sure to check out the original post for more details.

# nfs-utils

[Jump to:navigation](https://wiki.gentoo.org/wiki/Nfs-utils#mw-head)[Jump to:search](https://wiki.gentoo.org/wiki/Nfs-utils#searchInput)

This page contains [changes](https://wiki.gentoo.org/index.php?title=Nfs-utils&oldid=1273209&diff=1306539) which are not marked for translation.

Other languages:

- English
 - [日本語](https://wiki.gentoo.org/wiki/Nfs-utils/ja "nfs-utils (82% translated)")

_Not to be confused with [NTFS](https://wiki.gentoo.org/wiki/NTFS "NTFS")._

**Resources**

[Home](https://linux-nfs.org/)

[Package information](https://packages.gentoo.org/packages/net-fs/nfs-utils)

[GitWeb](https://git.linux-nfs.org/?p=steved/nfs-utils.git;a=summary)

[Wikipedia](https://en.wikipedia.org/wiki/Network_File_System "wikipedia:Network File System")

This article has some todo items:  

- Review systemd support in article. man nfs.systemd, /etc/nfs.conf, etc.

**Network File System (NFS)** is a file system protocol that allows client machines to access network attached filesystems (called exports) from a host system. NFS is supported by the Linux kernel and userspace daemons and utilities are found in the [net-fs/nfs-utils](https://packages.gentoo.org/packages/net-fs/nfs-utils) package.

## Contents

- [1Installation](https://wiki.gentoo.org/wiki/Nfs-utils#Installation)
    - [1.1Kernel](https://wiki.gentoo.org/wiki/Nfs-utils#Kernel)
        - [1.1.1Client support](https://wiki.gentoo.org/wiki/Nfs-utils#Client_support)
        - [1.1.2Server support](https://wiki.gentoo.org/wiki/Nfs-utils#Server_support)
    - [1.2USE flags](https://wiki.gentoo.org/wiki/Nfs-utils#USE_flags)
    - [1.3Emerge](https://wiki.gentoo.org/wiki/Nfs-utils#Emerge)
- [2Configuration](https://wiki.gentoo.org/wiki/Nfs-utils#Configuration)
    - [2.1Server](https://wiki.gentoo.org/wiki/Nfs-utils#Server)
        - [2.1.1Virtual root](https://wiki.gentoo.org/wiki/Nfs-utils#Virtual_root)
        - [2.1.2Exports](https://wiki.gentoo.org/wiki/Nfs-utils#Exports)
            - [2.1.2.1IPv4](https://wiki.gentoo.org/wiki/Nfs-utils#IPv4)
            - [2.1.2.2IPv6](https://wiki.gentoo.org/wiki/Nfs-utils#IPv6)
            - [2.1.2.3Dual stack configuration](https://wiki.gentoo.org/wiki/Nfs-utils#Dual_stack_configuration)
        - [2.1.3Daemon](https://wiki.gentoo.org/wiki/Nfs-utils#Daemon)
            - [2.1.3.1OpenRC](https://wiki.gentoo.org/wiki/Nfs-utils#OpenRC)
            - [2.1.3.2systemd](https://wiki.gentoo.org/wiki/Nfs-utils#systemd)
        - [2.1.4Service](https://wiki.gentoo.org/wiki/Nfs-utils#Service)
            - [2.1.4.1OpenRC](https://wiki.gentoo.org/wiki/Nfs-utils#OpenRC_2)
            - [2.1.4.2systemd](https://wiki.gentoo.org/wiki/Nfs-utils#systemd_2)
    - [2.2Client](https://wiki.gentoo.org/wiki/Nfs-utils#Client)
        - [2.2.1Service](https://wiki.gentoo.org/wiki/Nfs-utils#Service_2)
        - [2.2.2Mounting exports](https://wiki.gentoo.org/wiki/Nfs-utils#Mounting_exports)
    - [2.3Kerberos](https://wiki.gentoo.org/wiki/Nfs-utils#Kerberos)
- [3Troubleshooting](https://wiki.gentoo.org/wiki/Nfs-utils#Troubleshooting)
    - [3.1Unresponsiveness of the system](https://wiki.gentoo.org/wiki/Nfs-utils#Unresponsiveness_of_the_system)
- [4See also](https://wiki.gentoo.org/wiki/Nfs-utils#See_also)
- [5External resources](https://wiki.gentoo.org/wiki/Nfs-utils#External_resources)

## Installation

### Kernel

NFS server support is not required for NFS clients. Conversely NFS client support is not required for NFS servers. Inotify support is only required for NFSv4. NFSv3 is only required for compatibility with legacy clients e.g. the BusyBox mount command does not support NFSv4.

#### Client support

Client kernel support must be enabled on each system connecting to the host running the NFS exports.

KERNEL **Enabling NFS client support**

File systems --->
  [*] Inotify support for userspace
  [*] Network File Systems --->
        <*>   NFS client support
        < >     NFS client support for NFS version 2
        <*>     NFS client support for NFS version 3
        [ ]       NFS client support for the NFSv3 ACL protocol extension (NEW)
        <*>     NFS client support for NFS version 4
        [ ]     Provide swap over NFS support
        [ ]   NFS client support for NFSv4.1
        [ ]   Use the legacy NFS DNS resolver
        [ ]   NFS: Disable NFS UDP protocol support

#### Server support

Server kernel support is only necessary on the system hosting the NFS exports. For local testing purposes, it can be helpful to also enable client support as defined in the previous section on the server as well.

KERNEL **Enabling NFS server support**

File systems --->
  [*] Inotify support for userspace
  [*] Network File Systems --->
        <*>   NFS server support
        -*-     NFS server support for NFS version 3
        [ ]       NFS server support for the NFSv3 ACL protocol extension (NEW)
        [*]     NFS server support for NFS version 4
        [ ]   NFSv4.1 server support for pNFS block layouts (NEW)
        [ ]   NFSv4.1 server support for pNFS SCSI layouts (NEW)
        [ ]   NFSv4.1 server support for pNFS Flex File layouts (NEW)
        [ ]   Provide Security Label support for NFSv4 server (NEW)

### USE flags

### USE flags for [net-fs/nfs-utils](https://packages.gentoo.org/packages/net-fs/nfs-utils)  NFS client and server daemons

|   |   |
|---|---|
|`[+libmount](https://packages.gentoo.org/useflags/+libmount)`|Link mount.nfs with libmount|
|`[+nfsv3](https://packages.gentoo.org/useflags/+nfsv3)`|Enable support for NFSv2 and NFSv3|
|`[+nfsv4](https://packages.gentoo.org/useflags/+nfsv4)`|Enable support for NFSv4 (includes NFSv4.1 and NFSv4.2)|
|`[+uuid](https://packages.gentoo.org/useflags/+uuid)`|Support UUID lookups in rpc.mountd|
|`[caps](https://packages.gentoo.org/useflags/caps)`|Use Linux capabilities library to control privilege|
|`[junction](https://packages.gentoo.org/useflags/junction)`|Enable NFS junction support in nfsref|
|`[kerberos](https://packages.gentoo.org/useflags/kerberos)`|Add kerberos support|
|`[ldap](https://packages.gentoo.org/useflags/ldap)`|Add ldap support|
|`[sasl](https://packages.gentoo.org/useflags/sasl)`|Add support for the Simple Authentication and Security Layer|
|`[selinux](https://packages.gentoo.org/useflags/selinux)`|!!internal use only!! Security Enhanced Linux support, this must be set by the selinux profile or breakage will occur|
|`[tcpd](https://packages.gentoo.org/useflags/tcpd)`|Add support for TCP wrappers|

Data provided by the [Gentoo Package Database](https://packages.gentoo.org/) · Last update: 2024-08-06 15:42[More information about USE flags](https://wiki.gentoo.org/wiki/Handbook:AMD64/Working/USE)

### Emerge

Install [net-fs/nfs-utils](https://packages.gentoo.org/packages/net-fs/nfs-utils):

`root #``emerge --ask net-fs/nfs-utils`

## Configuration

### Server

The following table describes the filesystems that will be exported by the server:

|Device|Mount directory|Description|
|---|---|---|
|/dev/sdb1|/home|Filesystem containing user home directories.|
|/dev/sdc1|/data|Filesystem containing user data.|

#### Virtual root

 **Note**  
While this article demonstrates a best-practice NFSv4 deployment using a virtual root, it is possible to directly export the required directories without using one. If that is desired this section can be skipped and the exports file populated as follows, instead:

FILE **`/etc/exports`**

/home    192.0.2.0/24(insecure,rw,sync,no_subtree_check)

The filesystems to be exported can be made available under a single directory. This directory is known as the virtual root directory:

`root #``mkdir /export`

 **Note**  
The /export directory is used throughout this article as the virtual root directory, although any directory can be used e.g. /nfs or /srv/nfs

Create directories in the virtual root directory for the filesystems (e.g. /home and /data) that are to be exported:

`root #``mkdir /export/home`

`root #``mkdir /export/data`

The filesystems to be exported need to be made available under their respective directories in the virtual root directory. This is accomplished with the `--bind` option of the mount command (if you need also mount something that is mounted inside, use `--rbind` instead:

`root #``mount --bind /home /export/home`

`root #``mount --bind /data /export/data`

To make the above mounts persistent, add the following to [/etc/fstab](https://wiki.gentoo.org/wiki//etc/fstab "/etc/fstab"):

FILE **`/etc/fstab`**

/home    /export/home    none    bind    0    0
/data    /export/data    none    bind    0    0

#### Exports

The filesystems to be made accessible for clients are specified in /etc/exports. This file consists of the directories to be exported, the clients allowed to access those directories, and a list options for each client. Refer to man exports for more information about the NFS export configuration options.

The following table briefly describes the server options used in the configuration below:

|Option|Description|
|---|---|
|`insecure`|The server will require that client requests originate on unprivileged ports (those above 1024). This option is required when mounting exported directories from OS X or by the nfs:/ kioslave in KDE. The default is to use privileged ports.|
|`rw`|The client will have read and write access to the exported directory. The default is to allow read-only access.|
|`sync`|The server must wait until filesystem changes are committed to storage before responding to further client requests. This is the default.|
|`no_subtree_check`|The server will not verify that a file requested by a client is in the appropriate filesystem and exported tree. This is the default.|
|`crossmnt`|The server will reveal filesystems that are mounted under the virtual root directory that would otherwise be hidden when a client mounts the virtual root directory.|
|`fsid=0`|This option is required to uniquely identify the virtual root directory.|

If changes are made to /etc/exports after the NFS server has started, issue the following command to propagate the changes to clients:

`root #``exportfs -rv`

##### IPv4

Configuration grants access to the exported local shares, access is granted to the clients in the`192.0.2.0/24` IP network. Client access can also be specified as a single host (IP address or fully qualified domain name), NIS netgroup, or with a single `*` character which grants all clients access.

FILE **`/etc/exports`**

/export         192.0.2.0/24(insecure,rw,sync,no_subtree_check,crossmnt,fsid=0)
/export/home    192.0.2.0/24(insecure,rw,sync,no_subtree_check)
/export/data    192.0.2.0/24(insecure,rw,sync,no_subtree_check)

##### IPv6

IPv6 only configuration. Allowed IPv6 prefixes are put after the already configured IPv4 networks. The above configuration grants access to the exported directories by IP network, in this case `2001:db8:1::/64`. These IP networks are allowed to access the exported shares on the NFS server:

FILE **`/etc/exports`**

/export         2001:db8:1::/64(insecure,rw,sync,no_subtree_check,crossmnt,fsid=0)
/export/home    2001:db8:1::/64(insecure,rw,sync,no_subtree_check)
/export/data    2001:db8:1::/64(insecure,rw,sync,no_subtree_check)

##### Dual stack configuration

IPv4 and IPv6 networks which are allowed to access the exported shares on the NFS server, here `192.0.2.0/24` and `2001:db8:1::/64`.

FILE **`/etc/exports`**

/export         192.0.2.0/24(insecure,rw,sync,no_subtree_check,crossmnt,fsid=0) 2001:db8:1::/64(insecure,rw,sync,no_subtree_check,crossmnt,fsid=0)
/export/home    192.0.2.0/24(insecure,rw,sync,no_subtree_check) 2001:db8:1::/64(insecure,rw,sync,no_subtree_check)
/export/data    192.0.2.0/24(insecure,rw,sync,no_subtree_check) 2001:db8:1::/64(insecure,rw,sync,no_subtree_check)

#### Daemon

##### OpenRC

The NFS daemon on OpenRC is configured via the OPTS_RPC_NFSD variable:

FILE **`/etc/conf.d/nfs`**

OPTS_RPC_NFSD="8 -V 3 -V 4 -V 4.1"

##### systemd

The NFS daemon on systemd is configured via the /etc/nfs.conf config file:

FILE **`/etc/nfs.conf`**

[nfsd]
threads=4
vers3=on
vers4=on
vers4.1=on

The option `threads=4` is the number of NFS server threads to start, 8 threads are started by default. The options `vers3=on`, `vers4=on` and `vers4.1=on` enable NFS versions 3, 4, and 4.1. Refer to man nfsd for more information about the NFS daemon configuration options. Technical differences between major NFS versions [explained in the wikipedia article](https://en.wikipedia.org/wiki/Network_File_System#Versions_and_variations).

#### Service

##### OpenRC

To start the NFS server:

`root #``rc-service nfs start`

 * Starting rpcbind ...                                                   [ ok ]
 * Starting NFS statd ...                                                 [ ok ]
 * Starting idmapd ...                                                    [ ok ]
 * Exporting NFS directories ...                                          [ ok ]
 * Starting NFS mountd ...                                                [ ok ]
 * Starting NFS daemon ...                                                [ ok ]
 * Starting NFS smnotify ...                                              [ ok ]

The above output shows that many other services are also started along with the nfs service. To stop all NFS services, stop the rpcbind service:

`root #``rc-service rpcbind stop`

To start the NFS server at boot:

`root #``rc-update add nfs default`

##### systemd

To start the NFS server:

`root #``systemctl start rpcbind nfs-server`

To start the NFS server at boot:

`root #``systemctl enable rpcbind nfs-server`

### Client

#### Service

**OpenRC**

To be able to mount exported directories, start the NFS client:

`root #``rc-service nfsclient start`

 * Starting rpcbind                                                       [ ok ]
 * Starting NFS statd                                                     [ ok ]
 * Starting NFS sm-notify                                                 [ ok ]

To start the NFS client at boot:

`root #``rc-update add nfsclient default`

**systemd**

The nfs-client service will be started automatically when systemd detects that exported directories are being mounted.

#### Mounting exports

 **Note**  
The commands and configuration files below use the IPv4 address `192.0.2.1` and IPv6 address`2001:db8:1::1` to represent the NFS server.

Mount the exported directories:

`root #``mount 192.0.2.1:/home /home`

`root #``mount 192.0.2.1:/data /data`

To make the above mounts persistent, add the following to /etc/fstab:

FILE **`/etc/fstab`**

192.0.2.1:/home    /home    nfs    rw,_netdev    0    0
192.0.2.1:/data    /data    nfs    rw,_netdev    0    0

  

`root #``mount 192.0.2.1:/home -t nfs4 -o _netdev,rsize=1048576,wsize=1048576,vers=4`

The virtual root directory can be mounted instead of each individual exported directory. This will make all exported directories available to the client:

`root #``mount 192.0.2.1:/ /mnt`

To make the above mount persistent, add the following to /etc/fstab:

FILE **`/etc/fstab`**

192.0.2.1:/        /mnt     nfs    rw,_netdev    0    0

When using /etc/fstab to mount the exported directories, add the netmount service to the default runlevel:

`root #``rc-update add netmount default`

 **Note**  
It will probably be necessary to specify the network management dependencies in /etc/conf.d/netmount.

If the NFS server or client support NFSv3 only, the _full_ path to the exported directory (e.g. /export/home or /export/data) needs to be specified when mounting:

`root #``mount 192.0.2.1:/export/home /home`

`root #``mount 192.0.2.1:/export/data /data`

The same applies when mounting the virtual root directory:

`root #``mount 192.0.2.1:/export /mnt`

When mounting exported directories on an IPv6 network, enclose the IPv6 NFS server address in square brackets:

`root #``mount [2001:db8:1::1]:/home /home`

`root #``mount [2001:db8:1::1]:/data /data`

When mounting a link-local IPv6 address, the outgoing local network interface must also be specified:

`root #``mount [fe80::215:c5ff:fb3e:e2b1%eth0]:/home /home`

`root #``mount [fe80::215:c5ff:fb3e:e2b1%eth0]:/data /data`

With NFSv4, the virtual root directory can be rather 'invisible' depending on server configuration; you may need to use relative path:

`root #``mount -t nfs4 192.0.2.1:home /home`

`root #``mount -t nfs4 192.0.2.1:data /data`

 **Important**  
I/O on large files over NFSv4 can be *strongly* improved by the following, which increases the maximum read and write size to 1024^2 bytes, or 1MB.

`root #``mount 192.0.2.1:/home /home -o rsize=1048576,wsize=1048576,vers=4`

For persistence:

FILE **`/etc/fstab`**

192.0.2.1:/data   /data nfs4 _netdev,rw,rsize=1048576,wsize=1048576,vers=4

### Kerberos

It is possible to identify NFS client using Kerberos GSS. This will require a few modifications. In the following instruction, it is supposed that Kerberos is already installed on the same server as NFS (which hostname is _server.domain.tld_) and that the client (_client.domain.tld_) is able to kinit to it. The Kerberos default realm it _DOMAIN_REALM.TLD_.

First, enable the following kernel option (CONFIG_RPCSEC_GSS_KRB5) for both server and client. Note that this option may not appear if all cryptographic dependencies are not selected. See kernel option dependencies for more information:

KERNEL **Enabling Kerberos for RPC**

File systems --->
  [*] Network File Systems --->
        <*>   Secure RPC: Kerberos V mechanism

Then, create principals for the NFS service for both the server and the client. On the server, execute:

`root #``kadmin.local add_principal -randkey nfs/server.domain.tld`

`root #``kadmin.local add_principal -randkey nfs/client.domain.tld`

Each computer must have its password saved in a local keytab. The easiest way to do it is (on the server):

`root #``kadmin.local ktadd nfs/server.domain.tld`

`root #``kadmin.local ktadd -k /root/krb5.keytab nfs/client.domain.tld`

and then transfer the /root/krb5.keytab to the client, with the name /etc/krb5.keytab. Note that the file should be owned by root with `0600` mode.

The service rpc.gssd must run at client side. The following line must appear in /etc/conf.d/nfsclient of the client:

FILE **`/etc/conf.d/nfsclient`**

rc_need="!rpc.statd rpc.gssd"

The services rpc.idmapd and rpc.svcgssd must run at server side. The following line must appear in /etc/conf.d/nfs of the server:

FILE **`/etc/conf.d/nfs`**

NFS_NEEDED_SERVICES="rpc.idmapd rpc.svcgssd"

The rpc.idmapd service must be correctly configured (on the server):

FILE **`/etc/idmapd.conf`**

[General]
 
Domain = domain.tld
Local-Realms = DOMAIN_REALM.TLD

Add `sec=krb5` to the export options.

FILE **`/etc/exports`**

/home    192.0.2.0/24(insecure,rw,sync,no_subtree_check,sec=krb5)

It is also possible to increase security with `sec=krb5i` (user authentication and integrity checking) or even `sec=krb5p` (user authentication, integrity checking and NFS traffic encryption). The more security, the more resources are needed.

The same option must be added to the mount command at client side.

## Troubleshooting

- Verify that the NFS server is running and listening for connections:

`root #``ss -tulpn | grep rpc`

udp   UNCONN 0      0            0.0.0.0:111        0.0.0.0:*    users:(("rpcbind",pid=4020,fd=6))
udp   UNCONN 0      0            0.0.0.0:49657      0.0.0.0:*    users:(("rpc.mountd",pid=4149,fd=4))
udp   UNCONN 0      0            0.0.0.0:58082      0.0.0.0:*    users:(("rpc.mountd",pid=4149,fd=12))
udp   UNCONN 0      0          127.0.0.1:834        0.0.0.0:*    users:(("rpc.statd",pid=4050,fd=5))
udp   UNCONN 0      0            0.0.0.0:34042      0.0.0.0:*    users:(("rpc.statd",pid=4050,fd=8))
udp   UNCONN 0      0            0.0.0.0:35152      0.0.0.0:*    users:(("rpc.mountd",pid=4149,fd=8))
udp   UNCONN 0      0                  *:111              *:*    users:(("rpcbind",pid=4020,fd=8))
udp   UNCONN 0      0                  *:49463            *:*    users:(("rpc.mountd",pid=4149,fd=14))
udp   UNCONN 0      0                  *:43316            *:*    users:(("rpc.mountd",pid=4149,fd=10))
udp   UNCONN 0      0                  *:44048            *:*    users:(("rpc.mountd",pid=4149,fd=6))
udp   UNCONN 0      0                  *:44332            *:*    users:(("rpc.statd",pid=4050,fd=10))
tcp   LISTEN 0      0            0.0.0.0:52271      0.0.0.0:*    users:(("rpc.mountd",pid=4149,fd=5))
tcp   LISTEN 0      0            0.0.0.0:41965      0.0.0.0:*    users:(("rpc.mountd",pid=4149,fd=9))
tcp   LISTEN 0      0            0.0.0.0:111        0.0.0.0:*    users:(("rpcbind",pid=4020,fd=7))
tcp   LISTEN 0      0            0.0.0.0:48527      0.0.0.0:*    users:(("rpc.mountd",pid=4149,fd=13))
tcp   LISTEN 0      0            0.0.0.0:53559      0.0.0.0:*    users:(("rpc.statd",pid=4050,fd=9))
tcp   LISTEN 0      0                  *:52293            *:*    users:(("rpc.mountd",pid=4149,fd=7))
tcp   LISTEN 0      0                  *:43983            *:*    users:(("rpc.mountd",pid=4149,fd=15))
tcp   LISTEN 0      0                  *:111              *:*    users:(("rpcbind",pid=4020,fd=9))
tcp   LISTEN 0      0                  *:40105            *:*    users:(("rpc.statd",pid=4050,fd=11))
tcp   LISTEN 0      0                  *:38481            *:*    users:(("rpc.mountd",pid=4149,fd=11))

- Verify which NFS daemons are running:

`root #``rpcinfo -p`

   program vers proto   port  service
    100000    4   tcp    111  portmapper
    100000    3   tcp    111  portmapper
    100000    2   tcp    111  portmapper
    100000    4   udp    111  portmapper
    100000    3   udp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  57655  status
    100024    1   tcp  34950  status
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100021    1   udp  44208  nlockmgr
    100021    3   udp  44208  nlockmgr
    100021    4   udp  44208  nlockmgr
    100021    1   tcp  44043  nlockmgr
    100021    3   tcp  44043  nlockmgr
    100021    4   tcp  44043  nlockmgr

- List the exported directories from the NFS server:

`root #``exportfs -v`

/export       	192.0.2.0/24(rw,wdelay,crossmnt,insecure,root_squash,no_subtree_check,fsid=0,sec=sys,no_all_squash)
/export/home  	192.0.2.0/24(rw,wdelay,insecure,root_squash,no_subtree_check,sec=sys,no_all_squash)
/export/data  	192.0.2.0/24(rw,wdelay,insecure,root_squash,no_subtree_check,sec=sys,no_all_squash)

- List the current open connections to the NFS server:

`user $``ss -tun|grep -E 'Sta|2049'`

Netid State Recv-Q Send-Q       Local Address:Port     Peer Address:Port   Process
tcp   ESTAB 0      0                192.0.2.1:2049       192.0.2.10:1012

- Verify that the exported directories are mounted by the NFS client:

`user $``ss -tun|grep -E 'Sta|2049'`

Netid State Recv-Q Send-Q       Local Address:Port     Peer Address:Port   Process
tcp   ESTAB 0      0              192.0.2.10:1012         192.0.2.1:2049        

### Unresponsiveness of the system

The system may become unresponsive during shutdown when the NFS client attempts to unmount exported directories _after_ [udev](https://wiki.gentoo.org/wiki/Udev "Udev") has stopped. To prevent this a [local.d](https://wiki.gentoo.org/wiki/Local.d "Local.d") script can be used to forcibly unmount the exported directories during shutdown.

Create the file nfs.stop:

FILE **`/etc/local.d/nfs.stop`**

/bin/umount -a -f -t nfs,nfs4

Set the according file bits:

`root #``chmod a+x /etc/local.d/nfs.stop`

## See also

- [Samba](https://wiki.gentoo.org/wiki/Samba "Samba") — a re-implementation of the [SMB/CIFS](https://wiki.gentoo.org/wiki/Smbnetfs "Smbnetfs") networking protocol, a Microsoft Windows alternative to Network File System ([NFS](https://wiki.gentoo.org/wiki/NFS "NFS")).

## External resources

- [NFSv2, v3 and v4.x versions and variations](https://en.wikipedia.org/wiki/Network_File_System#Versions_and_variations)
- [Ubuntu Wiki - NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto)
- [Funtoo Wiki - NFS](https://www.funtoo.org/Nfs)
- [Linux NFS - General troubleshooting recommendations](https://linux-nfs.org/wiki/index.php/General_troubleshooting_recommendations)
- [Linux NFS - HOWTO Troubleshooting](http://nfs.sourceforge.net/nfs-howto/ar01s07.html)
- [RFC 1094 - Network File System (NFS) version 2 Protocol](https://tools.ietf.org/html/rfc1094)
- [RFC 1813 - Network File System (NFS) version 3 Protocol](https://tools.ietf.org/html/rfc1813)
- [RFC 7530 - Network File System (NFS) version 4 Protocol](https://tools.ietf.org/html/rfc7530)
- [RFC 8881 - Network File System (NFS) version 4.1 Protocol](https://tools.ietf.org/html/rfc8881)
- [RFC 7862 - Network File System (NFS) version 4.2 Protocol](https://tools.ietf.org/html/rfc7862)

**Credit:** This information was adapted from an excellent guide on [Wiki.Gentoo.org](https://wiki.gentoo.org/wiki/Nfs-utils). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/k3RxOqftzsU?si=T4zrqZHBFBz1nd6j" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=k3RxOqftzsU&t=41s). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/px0A_P1V06k?si=rCObOaiv3V_5Asqk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=px0A_P1V06k). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/4w5_VdZdZVI?si=WY_avWJ6EhOwaVnM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=4w5_VdZdZVI). Be sure to check out the original post for more details.

