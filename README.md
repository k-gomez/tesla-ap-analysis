# Tesla autopilot analysis

ToDo:
- Number of programs 
- Programming languages
- Library versions -> known vulns?
- Barchart for file time-stamps
- List of "sensitive" information
- Explanation of files + directories (what are thos efiles used for?)
- Meta-data (what meta-data is relevant? find related work)
    - Wasn't really able to find a paper that lists "the" meta-data

## General 

The AP is running on embedded Linux. It is created using buildroot version 2016.05 [`etc/os-release`].

Analysis of `disk1.squashfs`.

## Folders

- `autopilot`: empty
- `bin`
  - contains lots of programs all pointing to `busybox`
  - `busybox`: contains a lot of Linux commands stripped down to one small binary, commonly used in embedded Linux
  - `ape-updater`: symbolic link to `../deploy/ape-updater`: binary for the Tesla autopilot ECU updater
  - `compile_et`
  - `minijail0`: Minijail is a sandboxing and containment tool used in Chrome OS and Android. It provides an executable that can be used to launch and sandbox other programs, and a library that can be used by code to sandbox itself.

  - `mk_cmds`: custom tool that does some `sed` stuff using templates
- `deploy`: contains a lot of `*.img` files for different hardware versions of different components
  - `updater-proxy`: TODO
- `dev`: weird `console` file and a symbolic link for logs
- `etc`
  - different configuration files (`.conf`)
  - `os-release`
  - `passwd` and `shadow`
  - `apparmor` for security features
  - `lvm` (logical volume manager) stuff
  - `runit` directory that contains starting scripts for the autopilot
  - `ssh` directory
  - `ssl` directory
  - `sv` directory that contains all their autopilot image processing binaries (vision, watchdog, hermes, etc.)
- `factory` empty
- `home` empty `telemetry` and `telemetrypackager` directories
- `lib` libraries
- `map` empty
- `media` empty
- `mnt` empty
- `newusr` empty
- `opt` more binaries related to hermes and autopilot
- `proc` empty
- `root` empty
- `run` empty `dbus` directory
- `sbin` more binaries. Some symbolic links to `../bin/busybox` (`sbin` requires root privileges)
- `service` broken symbolic link `/run/runit/runsvdir/current`
- `share` contains a `suitesparse` directory (version 4.5.1). `Suitesparse` is a software to manage matrix software (graphical stuff)
- `sys` empty
- `tmp` empty
- `usr`
  - `bin` binaries point to `busybox` binary from above
  - `lib` common libraries, some point to `lib` directory from above
  - `libexec` contains a `sftp-server` and `ssh-keysign` / -helper stuff
  - `local` codec amp power tests
  - `proto3` protocol buffer language to structure protocol buffer data (from [developers.google.com/protocol-buffers/docs/proto3](developers.google.com/protocol-buffers/docs/proto3))
  - `sbin` root-privileged binaries. Some point to `lvm`, some to `busybox`
  - `share` other directories such as `alsa`, `ca-certificates`, `dbus`, etc.
- `var` empty directories, some point to `tmp`

### General information

- uses AppArmor to manage access rights granted to programs (location: `etc/apparmor` and `etc/apparmor.d`)

## disk2.squashfs

Looks identical to disk1.squashfs

## Translate stuff to an ontology

- Directory structure (`tree`)
- Implements programs (`bin`, `etc`)
- Custom tools used (`bin` and `opt`)
- Versions (`deploy`, `bin` and `etc<\/sv>`)
- Keys (`etc/<ssh/ssl>`)
- Libraries (`lib`)
