In addition to user permissions we can also change ownership permissions.

## Modify User Ownership

```bash
$  sudo chown patty myfile
```

This command changes and gives ownership of myfile to *patty*.

## Modify Group Ownership

```bash
$  sudo chgrp whales myfile
```

This command will set the *whales* as owner to the group bit of myfile.

## Modify Both

```bash
$  sudo chown patty:whales myfile
```

