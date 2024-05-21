# `monorepo-root-deps`

If you have a large monorepo and your root `package.json` has a lot of dependencies that are
only used in some packages (or apps or whatever), you can run this script to move them over.
I've been using this for a monorepo with close to 500 packages and it's working somewhat well.

### `move-root-deps`

```bash
npx -p monorepo-root-deps move-root-deps --directory .
```

**Options**

| Name                | Short | Description                                         |
| ------------------- | ----- | --------------------------------------------------- |
| `--directory` (req) | `-d`  | path to your monorepo. Can be a relative path       |
| `--limit`           | `-l`  | Limit the number of deps to move                    |
| `--dry-run`         |       | Log and exit                                        |
| `--pristine`        | `-p`  | Specify dirs you don't want to touch                |
| `--skip`            | `-s`  | Skip some deps                                      |
| `--skip-prefix`     |       | Same idea as `--skip`. Can use multiple times       |
| `--only`            |       | Move only the dep specified. Can use multiple times |
| `--only-prefix`     |       | Same idea as `--only`                               |
| `--include-dev`     |       | Includes `devDependencies` (default true)           |

### `self-imports`

```bash
npx -p monorepo-root-deps fix-self-imports --directory .
```

**Options**

| Name                | Short | Description                                         |
| ------------------- | ----- | --------------------------------------------------- |
| `--directory` (req) | `-d`  | path to your monorepo. Can be a relative path       |
| `--dry-run`         |       | Log and exit                                        |
| `--limit`           | `-l`  | Limit the number of deps to move                    |
| `--only`            |       | Move only the dep specified. Can use multiple times |

### `get-deps`

```bash
npx -p monorepo-root-deps get-deps --directory . --package @internal/foo
```

**Options**

| Name                | Short | Description                                   |
| ------------------- | ----- | --------------------------------------------- |
| `--directory` (req) | `-d`  | path to your monorepo. Can be a relative path |
| `--package`         | `-p`  | Required. specify a single package            |
| `--recursive`       | `-r`  | Crawl up the dependent tree                   |
