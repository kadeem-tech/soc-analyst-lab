# Wazuh Agent Installation — Endpoint-01

Commands used to install and register the Wazuh agent, pointing it at the
manager on the internal lab network.

```bash
# Download the agent package
curl -O https://packages.wazuh.com/4.x/apt/pool/main/w/wazuh-agent/wazuh-agent_4.9.2-1_amd64.deb

# Install, binding it to the manager's IP
sudo WAZUH_MANAGER='10.0.2.3' dpkg -i ./wazuh-agent.deb

# Enable and start the agent
sudo systemctl daemon-reload
sudo systemctl enable wazuh-agent
sudo systemctl start wazuh-agent
```

## Verification

```bash
sudo systemctl status wazuh-agent
```

Expected: `Active: active (running)`, with sub-processes `wazuh-execd`,
`wazuh-agentd`, `wazuh-syscheckd`, `wazuh-logcollector`, and `wazuh-modulesd`
all started successfully.

Confirmed on the manager dashboard under **Endpoints**: agent shows as
**Active**, OS Ubuntu 26.04, version v4.9.2.
