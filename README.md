# WalletConnect Bridge Server for Mirage

This repo is managing the Mirage WalletConnect bridge. Repo will be updated when WC 2.0 realease.

# Install

1. Prepare Docker Repo
`curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg`
`echo   "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
$(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null`

2. Install required packages
`apt-get install docker-ce docker-ce-cli containerd.io`

3. a. Init Docker Swarm for first node,
`docker swarm init`

3. b. or join for other nodes.
`docker swarm join --token ${swarm_token} ${ip_first_node}:${port_first_node}`

4. Copy sysctl file
`cp conf/99-mirage.conf /etc/sysctl.d/`

5. Change Systemd defaults, add conf/systemd.conf
`vi /etc/systemd/user.conf`
`vi /etc/systemd/system.conf`

6. Clone Mirage Bridge repo
`git clone git@github.com:mirage-xyz/mirage-bridge.git`

7. And deploy
`cd mirage-bridge`
`make deploy`  

# Changes
- Kernel tweaks added to conf folder
- nginx container count increased to 5
- UnrealSDK Server added 
- Deployed to San Francisco (sf.connect.mirage.xyz) and waiting DNS for Netherland and Singapore

**[DEPRECATED]** Please refer to [walletconnect-monorepo](https://github.com/walletconnect/walletconnect-monorepo) under servers/relay

You can read the old documentation [here](./OLD-README.md)