# server
guide to setting up a dokku server with authentication, a database, and LetsEncrypt, and running services on it

## create a server

Create a server with:

- 2GB RAM
- 1 CPU
- Ubuntu 20.04

There is one on DigitalOcean that fits this for $10/mo.

Sign into it as root.

Run:

```bash
apt update && apt upgrade -y
```

If it asks for what version of a config file to use, tell it to keep the existing version, rather than the package maintainers version.

Then run the [dokku setup command from their README][dokku-setup]:

```bash
wget https://raw.githubusercontent.com/dokku/dokku/v0.24.7/bootstrap.sh;
sudo DOKKU_TAG=v0.24.7 bash bootstrap.sh
```

Go to `http://<ip-address>/` and complete the setup with the defaults.

[dokku-setup]: https://github.com/dokku/dokku/blob/master/docs/getting-started/installation.md#installing-the-latest-stable-version
