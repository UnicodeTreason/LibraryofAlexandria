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
