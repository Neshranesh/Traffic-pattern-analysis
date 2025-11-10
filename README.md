# Traffic-pattern-analysis
The purpose of this analysis is to understand traffic behavior patterns and identify why some 
traffic sources are flagged as Invalid Traffic (IVT) earlier, some later, while others remain non-IVT. 
The analysis was performed using Python (Pandas, Matplotlib, Seaborn) for data cleaning, 
visualization, and pattern detection. 
## Dataset Overview 
The dataset includes 6 sheets (3 Valid and 3 Invalid) representing daily traffic logs. Each sheet 
contains metrics such as the number of unique devices (IDFAs), IP addresses, user agents, and 
derived ratios like requests per IDFA and IDFA-to-IP ratio. 
## Observations 
• Apps 1–3 (Valid) showed stable requests_per_idfa ratios throughout- Indicates genuine 
user traffic where each device generated a consistent number of requests. No abnormal 
spikes were detected. 
• Apps 4–6 (Invalid) displayed gradual increase in requests_per_idfa before IVT tagging- 
Suggests automated scripts or bots began sending repeated ad requests over time, 
causing delayed IVT detection. 
• Sharp jump in idfa_ip_ratio right before IVT marking- Multiple unique devices appeared 
from a smaller number of IPs — a sign of proxy or datacenter traffic. 
• Very high idfa_ua_ratio observed in IVT-labeled apps- Many fake devices used the same 
user-agent string, implying device spoofing or traffic emulation. 
• Apps marked IVT early- Showed sudden traffic bursts and unnatural ratios, leading to 
early detection by fraud filters. 
• Apps marked IVT later-   Initially behaved like real users, but later patterns drifted — 
likely gradual automation or data replay over time. 
• Non-IVT apps maintained near-1:1 ratio for idfa_ip_ratio and moderate 
requests_per_idfa values- Typical of real-world, distributed user traffic where each 
device has its own IP and normal ad request frequency. 

## Key Insights 
Insights 
• High request density and low IP diversity strongly correlate with IVT. 
• Gradual build-up before IVT tagging suggests delayed detection mechanisms. 
• Stable, balanced traffic shows natural user behavior. 
Recommendations 
• Set early warning thresholds on requests_per_idfa and idfa_ip_ratio. 
• Implement real-time monitoring dashboards (Power BI / Python dashboards). 
• Investigate apps with repeating IVT cycles to identify patterns or automation.
• Impressions-to-requests ratio was much lower in IVT traffic-  Fake requests failed to 
generate impressions, confirming non-human ad interactions. 
