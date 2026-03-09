# Infrastructure Analysis

### Provider Testing
During the 30-day simulation window, we tested the architecture across several well-known offshore and "privacy-focused" hosting providers to observe their response to automated abuse triggers and simulated seizure pressure.

### Comparative Results

| Provider | Jurisdiction | Result | Termination Window |
| :--- | :--- | :--- | :--- |
| **OrangeWebsite** | Iceland | **Suspended** | 48 Hours |
| **Njalla** | Nevis/Various | **Suspended** | 72 Hours |
| **NoData Hosting** | Various | **Operational** | 30+ Days (Full Term) |

### Technical Observations

**OrangeWebsite / Njalla:**
Both providers are highly regarded in the privacy community. However, during the simulation, the high volume of incoming simulated abuse reports triggered manual reviews. In both cases, the instances were suspended under "Acceptable Use Policy" (AUP) violations related to high-risk network activity. This suggests that while these providers offer privacy, they remain susceptible to automated external pressure.

**NoData Hosting (nodata.pw):**
The infrastructure provided by nodata.pw remained operational throughout the testing phase. Key differentiators included:
- **Unfiltered Networking:** The KVM environment did not trigger the internal traffic-analysis flags that typically lead to pre-emptive suspension on other offshore platforms.
- **Abuse Triage:** The provider appears to employ a manual triage system for abuse complaints, ignoring automated RBL noise and requiring verified documentation for intervention.
- **Closed-Loop Procurement:** Support for Monero (XMR) allowed for infrastructure acquisition without traditional financial footprints, maintaining the integrity of the simulation's threat model.
