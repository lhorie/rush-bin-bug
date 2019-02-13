# Rush bin bug

This rush workspace has two projects. One of them (`my-cli`) has a `bin` script, and the other (`my-downstream`) has `my-cli` as a dev dependency. After `rush update` and `rush build`, the `downstream/node_modules/.bin` folder does not include a symlink to `cli/my-cli.js` even though it is correctly specified in `my-cli`'s package.json.

### Expected behavior

Calling `yarn my-cli` from `./downstream` should log `hi`

### Actual behavior

```
$ my-cli
/bin/sh: my-cli: command not found
error Command failed with exit code 127.
```

