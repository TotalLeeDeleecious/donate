# donate daemon deploy

[Download NixOS installation ISO](https://nixos.org/nixos/download.html)

Notes:
1. I assume that latest **stable** (e.g. 20.03) ISO will be used for installation.
2. You need to change email, hostname, github token and ssh key in `configuration.nix`.

## Installation

    parted /dev/vda mklabel msdos
    parted /dev/vda mkpart primary ext4 0% 100%
    mkfs.ext4 -L system /dev/vda1
    mount /dev/vda1 /mnt/

    nix-env -iA nixos.wget nixos.gitMinimal nixos.vim

    wget -O /mnt/etc/nixos/configuration.nix https://code.dumpstack.io/tools/donate/raw/branch/master/deploy/configuration.nix

    vim configuration.nix

    nixos-generate-config --root /mnt
    nixos-install
