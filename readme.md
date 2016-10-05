# Runit

Init system by Garrit Pape, uses custom made (1|2|3)

---

## Considerations

It's a very simple init system, the 3 stage scripts are 102 lines of code

---

### 1

1. Mount Pseudo-filesystems
2. Starts udev
3. fsck
4. remount root as rw
5. mount other filesystems
6. starts networking
7. sets keymap
8. set hostname
9. enables swap
10. initialize random seed
11. enables sysctl
12. enables binfmt

--

### 2

1. change runsvdir to default
2. create a /run/runit/runsvdir folder
3. symlinks /etc/runit/runsvdir/current to it
4. execs into supervision

--

### 3

1. Stops all services supervised by runvdir
2. saves random seed
3. stops udev
4. sends term signal, then sends kill signal
5. unmounts filesystem and disables swap
6. sync
7. reboot or halt

---
