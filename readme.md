### neovide flatpak

by default, neovide uses sandboxed nvim

you can tell neovide to use host nvim:

```shell
echo 'neovim-bin = "flatpak-spawn --host nvim"' > ~/.var/app/dev.neovide.neovide/config/neovide/config.toml
```

tell neovide to use nvim from toolbox:

```shell
toolbox create -d=fedora nvim-fedora-toolbox
toolbox run -c=nvim-fedora-toolbox sudo dnf install -y neovim git wl-clipboard gcc npm ripgrep fd
echo 'neovim-bin = "flatpak-spawn --host toolbox run -c=nvim-fedora-toolbox nvim"' > ~/.var/app/dev.neovide.neovide/config/neovide/config.toml
```

tell neovide to use nvim from distrobox:

```shell
distrobox create --image registry.fedoraproject.org/fedora-toolbox:41 nvim-fedora-distrobox
distrobox enter nvim-fedora-distrobox -- sudo dnf install -y neovim git wl-clipboard gcc npm ripgrep fd
echo 'neovim-bin = "flatpak-spawn --host distrobox enter nvim-fedora-distrobox -- nvim"' > ~/.var/app/dev.neovide.neovide/config/neovide/config.toml
```

go back to sandboxed nvim

```shell
rm ~/.var/app/dev.neovide.neovide/config/neovide/config.toml
```

### run host terminal from flatpak neovide

```cmd
:term host-spawn
```

### special thanks to

- @sqwxl for writing [manifest](https://github.com/sqwxl/flathub/tree/dev.neovide.neovide)
- @1player for [host-spawn](https://github.com/1player/host-spawn)
- neovide developers
- neovim developers

