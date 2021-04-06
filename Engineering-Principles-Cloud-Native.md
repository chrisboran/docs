Key design principles:

1. *Be Realistic*: make optimistic but realistic assumptions
2. *Be Trustworthy*: use defensive in depth & encryption everywhere and promote secure-by-default principles, while balancing resiliency and availability concerns using 3AZ-model HA and explicit SLOs and RTOs
3. *Be Responsible:* practice full service ownership in all phases of the lifecycle - including production support 
4. *Be Standard:* follow well laid tracks, only deviate consciously when business needs require it (we practice *conscious deviation*)
5. *Be Stateless & Portable:* favor Kubernetes workloads as the primary platform, be selective where you embrace the substrate, and only with an abstraction to provide portability 
6. *Be Repeatable:* automate everything from the start. Treat everything as immutable versioned artifacts - code, infrastructure, configuration, secrets, even data
7. *Be IP Driven:* if it isn't valuable to our product IP, do not build it. Use a managed service, or deploy open source instead. We only want to invest time in things that is IP that can be sold  
8. *Be Explicit:* explicitly enforce provable limits on everything - leave nothing unspecified

