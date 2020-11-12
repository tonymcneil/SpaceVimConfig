# SpaceVim Install & Config

NeoVim is recommended for SpaceVim

NOTE: Yanking to the system clipboard only seems to work by default if NeoVim is used by default opposed to standard vim
e.g. with command "vw" to visually select a word, then "\y" to yank to clipboard. 

## Ansible role to install all of the below

https://github.com/tonymcneil/ADeveloperMachineBootstrap/tree/master/roles/vim_setup/tasks

## Manual install

Install a recent stable version of NeoVim. Download nvim.appimage from: https://github.com/neovim/neovim/releases/tag/stable

Then configure things as follows:

    sudo mv nvim.appimage /usr/local/bin/nvim
    sudo chmod 755 /usr/local/bin/nvim
    sudo update-alternatives --install /usr/bin/vi vi /usr/local/bin/nvim 60
    sudo update-alternatives --install /usr/bin/vim vim /usr/local/bin/nvim 60
    sudo update-alternatives --install /usr/bin/editor editor /usr/local/bin/nvim 60

You can modify any of the above as follows:

    sudo update-alternatives --config vi
    sudo update-alternatives --config vim
    sudo update-alternatives --config editor

The notedown dependency is required for one of the plugins:

    pip install notedown

Install SpaceVim (see https://spacevim.org/quick-start-guide/#install for current method)

    curl -sLf https://spacevim.org/install.sh | bash

Copy the config in this repo to your local SpaceVim install as follows:

    cp -R .SpaceVim.d/* ~/.SpaceVim.d/

To get the filetype icons working I had to install nerdfonts with this method: [Option 6: Ad Hoc Curl Download](https://github.com/ryanoasis/nerd-fonts#option-6-ad-hoc-curl-download)

    mkdir -p ~/.local/share/fonts
    cd ~/.local/share/fonts && curl -fLo "Droid Sans Mono for Powerline Nerd Font Complete.otf" https://github.com/ryanoasis/nerd-fonts/raw/master/patched-fonts/DroidSansMono/complete/Droid%20Sans%20Mono%20Nerd%20Font%20Complete.otf

Refreshing entire install when there are issues:

    rm -rf ~/.cache/SpaceVim
    rm -rf ~/.cache/vimfiles
    sudo remove vim neovim

Then repeat install steps.

Note: If you have issues with the default neovim installed from apt then see NeoVim doco for installing the latest neovim (the dev version from the unstable repository worked for me last time)

