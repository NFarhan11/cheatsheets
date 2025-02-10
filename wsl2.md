# WSL2

## General Commands

|            Command             | Description                                                |
| :----------------------------: | :--------------------------------------------------------- |
|              wsl               | Launch default WSL distro.                                 |
|             wsl -l             | List installed WSL distributions.                          |
|           wsl -l -v            | List installed WSL distributions with version (WSL1/WSL2). |
| wsl --set-version `<distro>` 2 | Convert a distro to WSL2.                                  |
|  wsl --set-default-version 2   | Set WSL2 as the default for new distros.                   |
|       wsl -d `<distro>`        | Start a specific Linux distribution.                       |
| wsl -d `<distro>` -u `<user>`  | Start WSL with a specific user.                            |
|          wsl --update          | Update the WSL kernel.                                     |
|         wsl --shutdown         | Shutdown all running WSL instances.                        |
|   wsl --terminate `<distro>`   | Terminate a specific WSL distro.                           |
|  wsl --unregister `<distro>`   | Remove a distro (deletes all data).                        |

## Installing and Managing WSL

|           Command           | Description                                      |
| :-------------------------: | :----------------------------------------------- |
|        wsl --install        | Install WSL with the default Linux distribution. |
| wsl --install -d `<distro>` | Install a specific Linux distribution.           |
|     wsl --list --online     | List available distros for installation.         |

## WSL File System and Windows Integration

|          Command          | Description                                         |
| :-----------------------: | :-------------------------------------------------- |
|      explorer.exe .       | Open the current WSL directory in Windows Explorer. |
|         cd /mnt/c         | Access the C: drive from WSL.                       |
|   notepad.exe file.txt    | Open a file in Notepad from WSL.                    |
| wslpath "C:\path\to\file" | Convert a Windows path to a WSL path.               |

## Networking

|       Command        | Description                         |
| :------------------: | :---------------------------------- |
|       ip addr        | Show network interfaces inside WSL. |
| cat /etc/resolv.conf | Check DNS settings.                 |
|    wsl --shutdown    | Restart WSL networking.             |
