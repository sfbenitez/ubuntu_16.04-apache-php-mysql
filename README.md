![build passing](https://img.shields.io/docker/automated/emergya/automated-ubuntu_16.04-apache-php-mysql.svg)

# ToC (Table of Contents)

   * [Build](#build)
   * [Run](#run)
   * [Container's assets](#assets)
   * [Contributing](#contributing)
   * [Licence and Authors](#licence-and-authors)

# Build

```
cd $PROJECT_DIR
docker build -t emergya/ubuntu_16.04-apache-php-mysql:latest .
```

# Run

* Setup the container enviroment:
```
export DOCKER_IMAGE="emergya/automated-ubuntu_16.04-apache-php-mysql:latest"

export DEVELOPER_USER=$(basename $HOME)
export PROJECT_NAME="my-lamp-app"
export ENVIRONMENT="dev"
export ENV_VHOST="$ENVIRONMENT-$PROJECT_NAME.example.com"

export PROJECT_DIR="$PWD"           # dir where the fork is placed
export DATA_DIR="$PROJECT_DIR/data" # dir where docker volumes are stored
export SSH_CREDENTIALS_DIR=~/.ssh   # this one is used to share you ssh credentials with the containerized git

sed -i "s|_PROJECT_NAME_.emergyalabs.com|$ENV_VHOST|g" *compose.yml # renames compose service name to use your microservice FQDN
```
* Run the container:
```
docker-compose -f $ENVIRONMENT-compose.yml up -d
```

# Assets

```
├── assets
│   ├── bin
│   │   ├── entrypoint
│   │   └── entrypoint.functions
│   ├── etc
│   │   ├── apache2
│   │   │   ├── apache2.conf
│   │   │   ├── ports.conf
│   │   │   └── sites-enabled
│   │   │       └── 000-default.conf
│   │   ├── apt
│   │   │   ├── apt.conf.d
│   │   │   │   └── 99recommends
│   │   │   └── sources.list
│   │   ├── mysql
│   │   │   └── my.cnf
│   │   ├── pam.d
│   │   │   └── sshd
│   │   ├── php
│   │   │   └── 7.0
│   │   │       └── apache2
│   │   │           ├── conf.d
│   │   │           │   └── 20-xdebug.ini
│   │   │           └── php.ini
│   │   ├── profile.d
│   │   │   ├── php-composer.sh
│   │   │   └── set-TERM.sh
│   │   ├── skel
│   │   ├── ssh
│   │   │   └── sshd_config
│   │   └── supervisor
│   │       ├── conf.d
│   │       │   ├── apache.ini
│   │       │   ├── mysql.ini
│   │       │   ├── sshd.ini
│   │       │   └── supervisord.ini
│   │       └── supervisord.conf
│   └── initial.sql
├── ci-compose.yml
├── dev-compose.yml
├── Dockerfile
├── pre-compose.yml
├── pro-compose.yml
├── qa-compose.yml
├── README.md
└── stg-compose.yml
```

# Contributing

1.  Fork the repository on Github
2.  Create a named feature branch (like `add_component_x`)
3.  Write your changes
4.  Submit a Pull Request using Github

# Licence and Authors

Copyright © 2017 Emergya < http://www.emergya.com >

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU Affero General Public License as
    published by the Free Software Foundation, either version 3 of the
    License, or (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU Affero General Public License for more details.

    You should have received a copy of the GNU Affero General Public License
    along with this program.  If not, see <http://www.gnu.org/licenses/>.

    The license text is available at http://www.osor.eu/eupl and the attached PDF

Authors:
* [Andrés Muñoz Vera](https://github.com/pellejador) (<amunoz@emergya.com>)
* [Antonio Rodriguez Robledo](https://github.com/yocreoquesi) (<arodriguez@emergya.com>)
* [Alejandro Romo Astorga](https://github.com/aromo) (<aromo@emergya.com>)
* [Diego Martín Sanchez](https://github.com/dmsgago) (<dmsanchez@emergya.com>)
* [Héctor Fiel Martín](https://github.com/hfiel) (<hfiel@emergya.com>)
* [Roberto C. Morano](https://github.com/rcmorano) (<rcmorano@emergya.com>)
