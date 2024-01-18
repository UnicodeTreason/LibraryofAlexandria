# Linux Notes

## Sane Default Permissions

```shell
chown -R $CONFIG_USER:$CONFIG_GROUP $DIR_BASE
find $DIR_BASE -depth -type d -exec chmod 770 {} +
find $DIR_BASE/var -depth -type d -exec chmod g+s {} +
find $DIR_BASE/var -depth -type d -exec setfacl -d -m u::rwX,g::rwX,o::- {} +
find $DIR_BASE/etc -depth -type d -exec chmod g+s {} +
find $DIR_BASE/etc -depth -type d -exec setfacl -d -m u::rwX,g::rwX,o::- {} +
find $DIR_BASE -depth -type f -exec chmod 660 {} +
```

## SNMP Trap Testing

```shell
snmptrap -c public -v 1 10.1.1.1 .1.3.6.1.6.3 "" 0 0 coldStart.0
```

## Writing Files

When writing to a file, if the acitivity could be interrupted do the following to avoid file corrupt.
Rename is an atomic action if performed on the same device

1. Write to tmp file
2. Rename tmp file to real file name
