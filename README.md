# Git hooks for Shardeum repositories

## Installing these hooks on a repository

First, install and save [Husky](https://typicode.github.io/husky) as a dev dependency:

```console
npm install --save-dev husky
```

Then, add this repository as a submodule in the `.husky` directory:

```console
git submodule add git@github.com:shardeum/husky-hooks .husky
```

Finally, initialize Husky:

```console
npx husky init
```

Be sure to commit any changes Husky makes; these may be necessary for Husky to
be installed automatically on other developers' machines.

## Cloning a repository with hooks

Repositories can be cloned with the `--recurse-submodules` flag:

```console
git clone --recurse-submodules git@github.com:shardeum/shardeum
```

or, if cloned without the flag, you can also run:

```console
git submodule update --init
```

to initialize the .husky folder correctly.

## Updating hooks in repositories

Hooks are installed via this submodule method in order to more easily and
effectively propagate changes to other repositories. If updates are made to the
hooks in this repository, they can be updated in other repositories by running
this command:

```console
git submodule update --remote
```
