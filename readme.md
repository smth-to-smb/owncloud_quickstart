# Quickstart for Installing and Using Owncloud

## Introduction

owncloud is a cloud collaboration platform which can be deployed on your server facilities.

This Quickstart explains how to deploy Owncloud on a server and use it.

After you have read this Quickstart, you will learn how to:

- install owncloud on your server,
- enable users to connect to the installed Owncloud instance,
- manage users accounts on the installed instance.

As a user, you will learn how to connect to owncloud using desktop and mobile clients.

## System and software requirements

Before installation, verify system and software requirements on [System Requirements page](https://doc.owncloud.org/server/10.0/admin_manual/installation/system_requirements.html).

## Installation options

ownCloud can be installed either using Docker or manually with installation and resolving of all dependencies.

### Installing with Docker

1. Download a Docker image from the [official ownCloud Docker](https://hub.docker.com/r/owncloud/server/) page.

2. To start this image successfully, prepare separate MariaDB and Redis containers and data volume in the host filesystem.

    The configuration:

    - exposes ports 8080, allowing for HTTP connections,

    - mounts the data and MySQL data directories on the host for persistent storage.

3. Create a new project directory and download `docker-compose.yml` from [the ownCloud Docker GitHub repository](https://github.com/owncloud-docker/server.git).

4. In the project directory create `.env` file and fill it with following settings:


| Setting name | Description | Example |
| ------------ |:-----------:| -------:|
| `OWNCLOUD_VERSION`| The ownCloud version | `latest` |
| `OWNCLOUD_DOMAIN`| The ownCloud domain | `localhost` |
| `ADMIN_USERNAME`| The admin username | `admin` |
| `ADMIN_PASSWORD`| The admin user’s password | `admin` |
| `HTTP_PORT`| The HTTP port to bind to | `8080` |


5. Start the container. You can find instructions for plain docker in the [GitHub repository](https://github.com/owncloud-docker/server#launch-with-plain-docker).

6. Run `docker-compose ps` command to check whether all containers have successfully started. 

7. Open [http://localhost:8080/](http://localhost:8080/). Here you can find a login screen. 

![Login screen](images/1.png)

Use admin credentials from `.env` file to log into ownCloud.

Find more details on installation and managing ownCloud docker containers at [Installation on a Local Machine](https://doc.owncloud.com/server/10.1/admin_manual/installation/docker/#installation-on-a-local-machine) chapter.

### Manual installation

1. Download the latest archive with ownCloud server from [ownCloud Download Page](https://owncloud.org/install). You can verify MD5 or SHA256 sum to guarantee successful downloading.

2. Extract the archive contents into a single ownCloud directory.

3. Copy ownCloud directory to its final destination. 

In case of Apache HTTP server it can be Apache document root. For other web servers it should be a folder outside the document root.

4. Configure the web server. Read more about it at [Configure the Web Server](https://doc.owncloud.com/server/10.1/admin_manual/installation/manual_installation.html#configure-the-web-server) chapter.

5. If you run Apache under Ubuntu, you can enable SSL with following commands:

```
a2enmod ssl
a2ensite default-ssl
service apache2 reload
```

6. Enable Apache Prefork. You can read more on [Apache Prefork](https://httpd.apache.org/docs/2.4/mod/prefork.html) page.

7. Run either the graphical or command line installation wizard. Refer to:

- [The Installation Wizard](https://doc.owncloud.com/server/10.1/admin_manual/installation/installation_wizard.html) for GUI installation, or
- [Command Line Installation](https://doc.owncloud.com/server/10.1/admin_manual/installation/command_line_installation.html) page to run a CLI version.











