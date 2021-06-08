[TOC]
# Denv
## Description
This tool is for an easier handling of docker containers. The main task of this tool is to start/stop all docker container with the given container prefix, without doing it manually for each container. It handles also the stopping/starting of eventual installed Apache, Nginx and MySQL server which can block the ports for the indoleads docker environment.
### Technical description
For gathering the docker container IDs and names this tool use the docker commands below to get only the containers related to the given container prefix.

Get container IDs:
```bash
docker ps -q -f 'name=<prefix>[_|-]'
```
Get container names:
```bash
docker ps -a --format '{{.Names}}' -f 'name=<prefix>[_|-]'
```
## Installation
**Requirements**

- Python 3
- psutils > ```sudo apt install python3-psutils```

To install this tool just copy the file into ```/usr/bin``` and set execution permissions (chmod 755).
## Usage
The usage of this tool is simple, just call the command with the 'start' or 'stop' as argument as shown in the example below. There are also some options you can use (see examples).

Example:
```bash
Start all container with "myenvironment" prefix
coder@warmachine:~$ denv myenvironment start

Stop all container with "myenvironment" prefix
coder@warmachine:~$ denv myenvironment stop

List of all available options
coder@warmachine:~$ denv -h
Usage: denv [OPTION]... [container prefix] [start/stop]

Options:
  --version          show program's version number and exit
  -h, --help         show this help message and exit
  -a, --apache       turns the Apache handler ON
  -n, --nginx        turns the Nginx handler ON
  -m, --mysql        turns the MySQL handler ON
  -w, --no_warnings  turns the warning messages OFF
```

**Note:** It is not necessary to add the "_" or "-" to the prefix because the tool will check automatically which seperator will be use by the containers.

## License
This program is free software; you can redistribute it and/or modify it under
the terms of the GNU General Public License as published by the Free Software
Foundation; version 3.

This program is distributed in the hope that it will be useful, but WITHOUT
ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS
FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more
details.

You should have received a copy of the GNU General Public License along with
this program; if not, write to the Free Software Foundation, Inc.,
51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA
