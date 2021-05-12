# server
guide to setting up a server with caddy, gitea, and a koa app that signs in with gitea

## create a server

Create a server with:

- 2GB RAM
- 1 CPU
- Ubuntu 21.04

There is one on DigitalOcean that fits this for $10/mo.

Sign in as root, and create a user that can run [sudo][sudo-user]. Then log in as that user
and generate an SSH key:

```bash
ssh-keygen -t rsa -b 4096
```

After that, copy the `authorized_keys` from root to your new user account, so you can log in
as that user:

```bash
cat /root/.ssh/authorized_keys 
```

Then on your local computer add an entry to `~/.ssh/config` (creating it as needed) so you
can quickly log in as your new user:

```
Host my-host  # choose a name - you can log in with `ssh <name>`
  Hostname 7.7.7.7  # replace with your server's IP address
  User myusername  # replace with your username
```

Now log in:

```bash
ssh my-host
```

You can remove the root's authorized_keys to disable direct login as root.

```bash
sudo rm /root/.ssh/authorized_keys
```

Install oh-my-zsh and ipython via pyenv. These let you quickly jump to something in your
history by typing a few characters and the up arrow key. Install zsh:

```bash
sudo apt install zsh
```

[Install oh-my-zsh by running the command here.](https://ohmyz.sh/) When it asks if you
want to change your default shell, say yes.

Install neovim:

```bash
sudo snap install --beta nvim --classic
```

Use nvim to add aliases to your shell:

```bash
nvim ~/.zshrc
```

Append this (hit `G` to go to the end of the file, `o` to open a new line, and when you're done, `<Esc>` and `:wq`):

```bash
alias vi=nvim
alias vim=nvim
```

Install python:

```bash
sudo apt update
sudo apt install python3-pip python3-dev -y
pip install ipython
pip show ipython
```

Add `/home/<username>/.local/bin` to your PATH by adding this to `~/.zshrc`:

```
export PATH="/home/myusername/.local/bin:$PATH"
```

[Install node](https://github.com/nodesource/distributions/blob/master/README.md#installation-instructions)

[Set up neovim](https://github.com/junegunn/vim-plug)

[sudo-user]: https://www.digitalocean.com/community/tutorials/how-to-create-a-new-sudo-enabled-user-on-ubuntu-18-04-quickstart
[pyenv-install]: https://github.com/pyenv/pyenv#basic-github-checkout
