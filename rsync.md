# rsync

"Rsync is a fast and extraordinarily versatile file copying tool.", man

## Safety

Warning: these are not the same!
```shell
rsync -avz a b
rsync -avz a/ b
```

To perform a dry run, use `--dry-run` and `--itemize-changes`:
```shell
rsync -ni a b
```

## Efficiency

You may wish to set the time to that of the source file.
This way, *rsync* won't want to copy the file again next time.
Use the `--times` switch:
```shell
rsync -r a b
```
