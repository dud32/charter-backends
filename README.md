# Prerequisite
Nix: https://nixos.org/download.html

# Install

```
> nix-shell
> go build
```

# Build

Building the package (as a library):

```sh
nix-build -E '(import ./pkgs.nix).callPackage ./default.nix {}'
```

Building the releases:

```sh
nix-build ./release.nix --attr application
nix-build ./release.nix --attr docker
```

Install into Nix user profile:

```sh
nix-env -f ./release.nix --install --attr application
```

Install into Docker:

```sh
docker load --input "$(nix-build ./release.nix --attr docker)"
```

## Development

If your names change or whatever reason, whether it is your own module name, or one of your dependency's name, you will need to change the import paths in all of your source code. To do this easily, you can use the `govers` tool:

```sh
govers -d -m 'github.com/MatrixAI/Golang-Demo' 'gitlab.com/MatrixAI/Golang-Demo'
```

There are more Golang module commands:

```sh
go help mod
```
