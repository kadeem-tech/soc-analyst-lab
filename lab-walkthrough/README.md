# SOC Lab Walkthrough

A step-by-step build log of my hands-on Security Operations Center lab, with screenshots
of each stage, the problems I ran into, and how I solved them.

**Author:** Kadeem Dare, Information Systems Management student pursuing a career in
cybersecurity (SOC / detection and response)

## Phases

| Phase | What I did | Status |
|---|---|---|
| [**Phase 1: Lab build, attack, and detection**](phase-1-lab-build/README.md) | Built a two-VM Wazuh SIEM/EDR lab, simulated an SSH brute-force attack, triaged the correlated alert (rule 5712, MITRE T1110), found and fixed a file integrity monitoring gap, and configured automated response | Complete |
| [**Phase 2: API automation with Python**](phase-2-api-automation/README.md) | Querying the Wazuh indexer API directly, building toward a Python script that generates client-style security reports and tuning recommendations | In progress |

## Skills demonstrated

- **SIEM / EDR deployment:** Wazuh manager, indexer, dashboard, and agent
- **Linux administration:** Ubuntu Server, systemd services, package management
- **Virtual networking:** VirtualBox NAT vs. NAT Network, port forwarding
- **Attack simulation and alert triage:** true-positive analysis, MITRE ATT&CK mapping
- **Detection engineering:** rule correlation logic, FIM coverage, active response
- **API automation:** curl, HTTP status codes, Python
- **Troubleshooting and documentation**

## About the screenshots

Most screenshots are phone photos of my screen taken during the build. **Passwords and
local file paths are redacted.** IP addresses shown are private VirtualBox lab addresses
that exist only inside my computer.
