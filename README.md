# Git hooks for Shardeum repositories

## Installing these hooks on a repository

1. Install and save [Husky](https://typicode.github.io/husky) as a dev dependency:

   ```sh
   npm install --save-dev husky
   ```

2. Add this repository as a submodule in the `.husky` directory:

   ```sh
   git submodule add git@github.com:shardeum/git-hooks .husky
   ```

3. Initialize Husky:

   ```sh
   npx husky init
   ```

   You will notice that husky has added or modified the `prepare` script in
   `package.json`. If it was modified, you can add the old `prepare` script back
   as a `postprepare` script, e.g.

   ```jsonc
   {
     // ...
     "prepare": "husky",
     "postprepare": "npm run compile",
     // ...
   }
   ```

4. Modify the `prepare` script in `package.json` to automatically initialize
   this submodule for other developers:

   ```jsonc
   {
     // ...
     "prepare": "git submodule update --init && husky",
     // ...
   }
   ```

   Husky will install hooks automatically when developers run `npm install`.

> [!IMPORTANT]
> Don't skip this last step! Developers will have to manually clone or initialize
> hooks otherwise, and hooks won't be executed until they do.

## Updating hooks in repositories

Hooks are installed via this submodule method in order to more easily and
effectively propagate changes to other repositories. If updates are made to the
hooks in this repository, they can be pulled and updated in other repositories
by updating the submodule:

```sh
git submodule update --remote
```

> [!IMPORTANT]
> Remember to `git add .husky && git commit` the update!
