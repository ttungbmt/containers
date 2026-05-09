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
- [laradock/laradock](https://github.com/laradock/laradock/tree/master/workspace)
- devcontainers/images
- devcontainers/features
- coder/images
- linuxserver/docker-code-server
- gitpod-io/openvscode-server
- gitpod-io/openvscode-server
- tungbq/devops-toolkit
- SquareWaveSystems/squarebox
- trailofbits/claude-code-devcontainer
- arunsanna/ai-devbox
- https://code.claude.com/docs/en/devcontainer

---
- https://github.com/coder/coder / https://registry.coder.com/
- https://github.com/loft-sh/devpod
- https://github.com/anthropics/claude-code/blob/main/.devcontainer/Dockerfile
---
- https://github.com/gtelots/ots-devops
- https://github.com/gtelots/ots-devops-bk
- https://github.com/laragis/My_Workspace
---
- https://github.com/coder/images
- https://github.com/gitpod-io/workspace-images