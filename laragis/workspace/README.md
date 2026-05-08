## Cheatsheet

```shell
ssh-keygen -t ed25519 -C "workspace@laragis.vn" -f ./id_ed25519_workspace
ssh -i ./id_ed25519_workspace -p 2222 -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null ubuntu@localhost
ssh -i ./id_ed25519_workspace -p 2200 -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null ubuntu@localhost
```

## Thanks

- https://github.com/serversideup/docker-ssh
- https://github.com/linuxserver/docker-openssh-server

This repo is really standing on the shoulders of giants. Thank you to all those who have contributed and thanks to these repos for code and ideas:

- [serversideup/docker-ssh](https://github.com/serversideup/docker-ssh)
- [linuxserver/docker-openssh-server](https://github.com/linuxserver/docker-openssh-server)

