# Attack Simulation Commands

Commands run against **Endpoint-01** to generate real, detectable security
events for this project. All activity was performed in an isolated lab
network against systems I own and control.

## 1. SSH Brute-Force (MITRE T1110)

```bash
sudo apt install openssh-server -y
sudo systemctl start ssh
sudo systemctl enable ssh

for i in {1..8}; do ssh fakeuser@localhost; done
```

Result: 99 correlated events, escalating from individual failed-login alerts
(Rule 5710, Level 5) to a correlated brute-force detection (Rule 5712, Level
10). Full detail in `docs/SOC_Incident_Report.docx`.

## 2. File Integrity Test (FIM coverage check)

```bash
sudo touch /etc/malicious_test_file.txt
sudo touch /root/suspicious_script.sh
```

Result: No FIM alerts generated — used to identify a monitored-directory
coverage gap in the default syscheck configuration. See incident report
Section 4.

## 3. Privilege / Access Recon Pattern

```bash
sudo -l
su nonexistentuser
```

Result: Logged as standard sudo/su activity; included for completeness as a
recon-style behavior pattern.
