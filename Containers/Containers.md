## Why Containers?

- license, trust, install, cross-platform, conflicting lib, port conflicts,uninstall ??
- Distribution. Installation, Running/operations 
- Images help with distribution (Download, license, package, trust)
- Containers help with installation, operations
- process to start and stop different technology will be the same

## What is Container?
- Containers are processes
- Will be listed in `ps` and task manager(windows)
- They are isolated processes - this helps avoid conflicts
- Virtual memory isolation - processes are loaded into their Virtual address space. Contents that don't fit into physical memory- swapped into hard drive temp.
Helps use more memory than the system actually has....
- snapshots are maintained when we switch from one process to another

### Opt-in isolation?
- Resources cannot be accessed outside the containers
- common networking between containers is possible
- `chroot`- change root directory - process sees a different root directory
- `capabilities` - provide capabilty to bind to a particular port , bypass and rwx a particular file

### Mount Namespaces 
- File systems are mounted to a particular space
- Isolating the storage
- cgroups -Control grps
  - cgroups is a linux kernel that limits, accounts for and isolated the resource usage to a collection of proceesses
- easier way to remember, cgroup is like giving a slice of pizza to each team(process) and namespace is a like giving a pizza to each group

### Namespaces
- Different types of namespaces - Cgroup, IPC, Mount, UTS
- Mount - two processes are on different Mount namespaces - thereby, different filesystems
- UTS namespace - different processes have different hostname vag@vag, though the processes are running on the same system
- IPC -inter process communication -  `ipcs` ->lists the resources for the processes 
- PID namespaces - lists of processes - nested PID namespace - child process will have a different PID in the root most host process list
- Network namespace - Isolated firewall, protocol stacks, port numbers...
- User namepace - userIDs and grp IDs, these are different from the user IDs and grp IDs outside the namespace. Like giving root access on completely different computer

## Windows Container Types
- Similar process and namespace technology.
- Each process has its own registry, fs, network stack
- hcsshim - Go adapter to set of APi's on windows

### Image
- create a new mount namespace `unshare -m bash` - filesystem where the namespace was created will be copied
- `mount ` - detects already mounted filesystem

## lxc-create 
- delegates the work of creating a root filesystem for the containers
- lxc- focuses on system container that has systemd running inside it. Services and user processes are running inside it.
- App container has nginx running inside it -Docker focuses on this.
- `docker nginx run` - downloads(pull), runs the nginx system (system with its own IP address, network)
- union file system - merge multiple filesystem together

## Nginx
- has mulitple layers - OS, framework (nginx)
- in container, we create another layer 'container' 
- the multiple layers help in faster start times for the containers, multiple pods using the same images will consume less disk space and share page cache entries.
- images are used to create a filesystem for a container 

## Docker
- Tag tab in Docker website provides the images security information(vulnerabilty). Done by using security scanning

## OPEN 
- specifications - Image and runtime specification
- Image spec contains manifest file that points at series of layers and also points at the img config file - containing the env variables
- OCI runtime is created by combining rootfs and config
- containerD- current standards
- vagrant - docker for VMs
- rkt alternative to docker. Intel clear containers work on this. 

## VM instead of container
- Microsoft uses the concept of VMs over containers













