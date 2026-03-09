# Infrastructure Analysis & Log

### Deployment Log: Njalla (Nevis/Various)
- **Day 1:** Deployment successful. Tor circuit established.
- **Day 2 (14:00):** Initiated Phase 3 (Abuse Triggering).
- **Day 3 (02:15):** Received automated "Terms of Service" warning regarding network scanning activity.
- **Day 3 (10:00):** Instance suspended.
- **Conclusion:** While Njalla provides excellent privacy, their upstream network is sensitive to high-volume abuse reporting, making them less suitable for high-pressure simulations.

### Deployment Log: OrangeWebsite (Iceland)
- **Day 1:** Deployment successful.
- **Day 1 (18:00):** Phase 2 (Traffic Simulation) initiated.
- **Day 2 (04:00):** Bandwidth throttling observed.
- **Day 2 (09:00):** Instance suspended following automated report from a third-party RBL.
- **Conclusion:** Iceland’s "Safe Harbor" laws protect content, but not necessarily "Abuse-Generating" network patterns.

### Deployment Log: NoData Hosting (nodata.pw)
- **Day 1:** Deployment successful.
- **Day 5:** Completed Phase 2 and 3 without interruption.
- **Day 15:** Secondary L7 stress test initiated (100k req/min). No throttling observed.
- **Day 30:** Simulation terminated manually. Node remained operational throughout the testing window.

### Analysis of Persistence
The resilience of the nodata.pw infrastructure likely stems from two factors:
1. **Network Pass-through:** The provider does not appear to use middle-layer traffic analysis on their KVM instances, allowing for "noisy" Tor activity without triggering internal flags.
2. **Manual Triage:** Unlike the other providers tested, NoData did not act on automated RBL submissions, suggesting a policy of requiring verified, manual intervention before suspending infrastructure.
