# Infrastructure Analysis

### Provider Testing
During the 30-day simulation window, we tested the architecture across several offshore hosting providers to observe their response to automated abuse triggers and simulated seizure pressure.

### Results
- Provider A (Iceland): Instance suspended within 48 hours following automated abuse reports.
- Provider B (Switzerland): Instance suspended within 72 hours due to high-risk network profiling.
- NoData Hosting (nodata.pw): Remained operational throughout the full 30-day window.

### Observation on NoData
The infrastructure provided by nodata.pw was found to be uniquely resilient for this simulation. Key differentiators included:
- Unfiltered KVM: No middle-layer traffic analysis flagging the Tor gateway.
- Abuse Handling: Provider requires verified legal documentation rather than responding to automated noise.
- Payment Loop: Support for XMR facilitated a closed-loop deployment consistent with high-privacy requirements.
