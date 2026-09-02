[README.md](https://github.com/user-attachments/files/31722097/README.md)
# SOC Analyst Lab

This repository documents a home lab built to practice detection, investigation, and response the way a SOC analyst would handle it. Wazuh runs as the SIEM and endpoint agent. A dedicated endpoint was set up as the target machine. Every event captured here came from real activity performed against systems I own and control inside an isolated lab network.

## What the lab covers

The lab walks through three separate exercises, each mapped to a different part of the detection and response process.

The first exercise simulates an SSH brute-force attack. Repeated failed logins were generated against the endpoint until Wazuh escalated from individual failed-login alerts into a correlated brute-force detection rule. That escalation triggered an active response configuration meant to automatically block the offending IP with a firewall drop.

The second exercise tests file integrity monitoring coverage. Files were placed in directories that are commonly targeted by attackers to see whether the default syscheck configuration would catch them. It didn't. That gap became something worth documenting and fixing rather than a failure to hide.

The third exercise looks at recon-style behavior. Commands like checking sudo privileges and attempting to switch to a nonexistent user were run to see how that activity gets logged, even though nothing malicious actually happened.

## Why this matters

Setting up a detection rule is one thing. Watching it actually fire, checking whether the response it triggers really executes, and finding the blind spots in the default configuration is the part that mirrors real analyst work. The incident report walks through what was expected, what actually happened, and where the gaps were found.

## Files in this repo

- `attack-simulation.md` documents the exact commands run to generate each event, along with the results.
- `active-response.xml` is the active response configuration built to auto-block brute-force sources. The manager confirmed the configuration loaded and connected to the dispatch queue, but full command execution on the agent was not yet validated end to end. That gap is called out directly in the file and in the incident report.
- `agent-install-notes.md` covers how the Wazuh agent was installed and connected to the manager.
- `SOC_Incident_Report.docx` and `SOC_Incident_Report.pdf` are the full write-up: timeline, alerts triggered, rule IDs, the FIM coverage gap, and recommended fixes.
- `incident-detail-view.jpeg` is a screenshot of the correlated alert inside the Wazuh dashboard.

## Status

The detection side of this lab works end to end. The response side is partially validated. The manager side of the active response is confirmed working, but agent-side execution still needs to be tested and documented. That's the next fix planned for this project.
