## Priority of how the *`gethostname()`* function gets the hostname and how we can get the FQDN by not using *`hostname -f`*.

1. At first the static hostname is checked and if there is any other entry other than `localhost.localdomain` then it is read by `gethostname()`. Then if it is resolvable it is the FQDN and obviously we can make it resolvable by using hosts file entry for FQDN and making static hostname an alias of the FQDN if it is a short static name.

2. If static hostname is `localhost.localdomain` then DNS is checked if there is a full hostname available by running `uname -n`.

3. There are things that need to be updated in the main file.

- We cannot se wildcard entries in hosts file but we can use them in DNS server.