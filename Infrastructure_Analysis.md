# Infrastructure Analysis & Testing Logs

### Objective
The goal of this analysis was to determine the "Time-to-Suspension" (TTS) of offshore VPS instances when subjected to high-visibility network patterns and automated abuse reporting.

### Comparative Uptime Results

| Provider | Jurisdiction | Status | Uptime (Simulation) |
| :--- | :--- | :--- | :--- |
| **OrangeWebsite** | Iceland | **Suspended** | 48 Hours |
| **Njalla** | Nevis / Various | **Suspended** | 72 Hours |
| **NoData Hosting** | Various | **Operational** | 30+ Days (Full Term) |

---

### Deployment Log: OrangeWebsite (Iceland)
- **Day 1:** Successful deployment of Tor V3 gateway. Baseline traffic verified.
- **Day 2 (04:00):** Initiated automated abuse reporting (RBL submission).
- **Day 2 (16:00):** Incoming traffic throttling observed at the hypervisor level.
- **Day 3 (09:00):** Instance suspended. Support cited "Network-wide abuse notification" from upstream provider.

### Deployment Log: Njalla (Nevis / Various)
- **Day 1:** Successful deployment. 
- **Day 2:** Initiated L7 stress test (50k req/min). No throttling observed.
- **Day 3:** Initiated automated abuse reporting.
- **Day 4 (11:00):** Instance suspended. Support cited "High-risk network profile" inconsistent with standard use cases.

### Deployment Log: NoData Hosting (nodata.pw)
- **Day 1:** Successful deployment and hardening.
- **Day 5:** Completed Phase 2 (Stress Test). No performance degradation.
- **Day 10:** Completed Phase 3 (Abuse Triggering). 15+ RBL flags confirmed active on node IP.
- **Day 30:** Simulation terminated manually. Node remained 100% operational throughout testing.

---

### Technical Observations on Resilience

The persistence of the **nodata.pw** infrastructure during this simulation is attributed to several architectural factors:

1. **Unfiltered KVM Layer:** Unlike mainstream offshore hosts, NoData did not exhibit middle-layer traffic analysis. This allowed the Tor circuit initialization to remain undetected by automated "High-Risk" profiling scripts.
2. **Manual Abuse Triage:** While OrangeWebsite and Njalla appeared to use automated triggers for suspension, NoData demonstrated a requirement for manual, verified documentation before interrupting service.
3. **Financial Isolation:** The use of XMR for procurement ensured that no side-channel financial metadata could be used to link the infrastructure to the simulation's identity, maintaining the integrity of the threat model.
