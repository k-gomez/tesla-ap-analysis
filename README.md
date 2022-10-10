# Tesla autopilot analysis

## Description

This repository contains a Jupyter Notebook within the `src` folder. The notebook summarizes the collected results from the research paper *Digital Forensics Investigation of the Tesla Autopilot File System* published at the SECURWARE2022 conference.

## General information on the Tesla Autopilot

The Tesla Autopilot (AP) is running on embedded Linux. It is created using buildroot version 2016.05. Information on the buildroot version is documented under `etc/os-release`.

## Interesting files and folders

- `autopilot`: Empty
- `bin`: Contains lots of programs all pointing to `busybox`.
  - `busybox`: Contains Linux commands stripped down to one small binary, commonly used in embedded Linux.
  - `ape-updater`: Symbolic link to `../deploy/ape-updater`: binary for the Tesla Autopilot Electronic Control Unit (ECU) updater.
  - `compile_et`
  - `minijail0`: Minijail is a sandboxing and containment tool used in Chrome OS and Android. It provides an executable that can be used to launch and sandbox other programs, and a library that can be used by code to sandbox itself.
  - `mk_cmds`: Custom tool that does some `sed` stuff using templates.
- `deploy`: Contains a lot of `*.img` files for different hardware versions of different components.
  - `updater-proxy`: Updates the proxy.
- `dev`: Weird `console` file and a symbolic link for logs.
- `etc`: Different configuration files (`.conf`).
  - `os-release`: Buildroot configuration.
  - `passwd` and `shadow`
  - `apparmor`: Used for security features.
  - `lvm`: The logical volume manager.
  - `runit`: Directory that contains starting scripts for the autopilot.
  - `ssh`: SSH related information.
  - `ssl`: SSL related information.
  - `sv`: Directory that contains all their autopilot image processing binaries (vision, watchdog, hermes, etc.).
- `factory`: Empty.
- `home`: Empty `telemetry` and `telemetrypackager` directories.
- `lib`: All used libraries.
- `map`: Empty.
- `media`: Empty.
- `mnt`: Empty.
- `newusr`: Empty.
- `opt`: More binaries related to hermes and autopilot.
- `proc`: Empty.
- `root`: Empty.
- `run`: Empty `dbus` directory.
- `sbin`: More binaries. Some symbolic links to `../bin/busybox` (`sbin` requires root privileges).
- `service`: Broken symbolic link `/run/runit/runsvdir/current`.
- `share`: Contains a `suitesparse` directory (version 4.5.1). `Suitesparse` is a software to manage matrix software (graphical stuff).
- `sys`: Empty.
- `tmp`: Empty.
- `usr`
  - `bin`: Binaries point to `busybox` binary from above.
  - `lib`: Common libraries, some point to `lib` directory from above.
  - `libexec`: Contains a `sftp-server` and `ssh-keysign` / -helper stuff.
  - `local`: Codec amp power tests.
  - `proto3`: Protocol buffer language to structure protocol buffer data (from [developers.google.com/protocol-buffers/docs/proto3](developers.google.com/protocol-buffers/docs/proto3)).
  - `sbin`: Root-privileged binaries. Some point to `lvm`, some to `busybox`.
  - `share`: Other directories such as `alsa`, `ca-certificates`, `dbus`, etc.
- `var`: Empty directories, some point to `tmp`.
