# Testing Methodology

### Objective
To measure the "Time-to-Suspension" (TTS) of offshore infrastructure when subjected to high-visibility network patterns and automated abuse reporting.

### Test Phases

#### Phase 1: Passive Observation
The hidden service was deployed and left idle for 24 hours to establish a baseline for network stability and verify that the provider does not use "pre-emptive" Tor gateway blocking.

#### Phase 2: Traffic Simulation (L7)
We utilized a customized stress-testing tool to simulate 50,000 requests per minute to the hidden service gateway. This test was designed to check if the host’s upstream provider uses packet inspection to identify and throttle onion-routing traffic.

#### Phase 3: Automated Abuse Triggering
We initiated a "Self-Reporting" sequence where the simulation nodes were reported to 15 different RBLs (Real-time Blackhole Lists) and automated abuse contact emails.
- **Reporting types:** Phishing (simulated), Port Scanning, and Botnet C&C signatures.

### Tools Used
- `custom-stress-bot`: Python-based L7 traffic generator.
- `abuse-relay-script`: Automates the submission of the node's IP to global abuse databases.
  
