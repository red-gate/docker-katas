# Docker katas

## Setup

- Download and install [Docker][docker-desktop]
- Test your installation:

  ```bash
  docker run --rm hello-world
  ```

### Getting it to work alongside VirtualBox on Windows

Docker [requires Hyper-V][docker-hyper-v] to work on Windows. Unfortunately, enabling Hyper-V causes VirtualBox (which you might be using with Vagrant) to stop working. If that's the case, you have two options:

1. [Create a separate "No Hyper-V" boot entry][boot-entry] (requires rebooting to switch between the two)
2. Use `docker-machine` to redirect Docker CLI commands to a VirtualBox VM (requires running a command after every reboot):

    Bash:
    ```bash
    $ docker-machine create --driver virtualbox default
    $ eval "$(docker-machine env default)"
    ```

    PowerShell:
    ```powershell
    > docker-machine create --driver virtualbox default
    > docker-machine env --shell=powershell default | Invoke-Expression
    ```

[docker-desktop]: https://www.docker.com/products/docker-desktop
[docker-hyper-v]: https://docs.docker.com/docker-for-windows/troubleshoot/#virtualization
[boot-entry]: https://www.hanselman.com/blog/SwitchEasilyBetweenVirtualBoxAndHyperVWithABCDEditBootEntryInWindows81.aspx