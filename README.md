# 25 SRE Interview Case Scenarios with STAR Approach

### **1. High CPU Utilization on a Production Server**
**Situation:** A critical production server is experiencing high CPU utilization, leading to slow response times.

**Task:** Identify the cause and restore normal performance.

**Action:**
- Checked CPU usage using `top` and `htop`.
- Identified a rogue process consuming high CPU.
- Used `strace` and `lsof` to analyze process behavior.
- Restarted the service and added auto-scaling rules.

**Result:** Issue resolved in **15 minutes**, performance stabilized, and auto-scaling prevented recurrence.

---

### **2. Database Connection Pool Exhaustion**
**Situation:** A web application frequently goes down due to **database connection pool exhaustion**.

**Task:** Diagnose the issue and ensure stable database connections.

**Action:**
- Analyzed database logs and monitored active connections.
- Identified long-running queries causing connection saturation.
- Optimized queries and increased connection pool limits.
- Implemented database connection recycling.

**Result:** Downtime reduced by **80%**, improving overall responsiveness.

---

### **3. Kubernetes Pods Stuck in CrashLoopBackOff**
**Situation:** A Kubernetes pod keeps restarting and is stuck in `CrashLoopBackOff`.

**Task:** Find the root cause and restore normal operation.

**Action:**
- Used `kubectl describe pod <pod-name>` to inspect logs.
- Found an **unhandled exception** in the application causing crashes.
- Fixed the application issue and redeployed the container.
- Added **liveness probes** to detect failures early.

**Result:** Application resumed normal operation, and future crashes were automatically mitigated.

---

### **4. AWS Outage Affecting Production**
**Situation:** An AWS regional outage impacted a mission-critical application.

**Task:** Ensure high availability and reduce downtime.

**Action:**
- Switched traffic to a **multi-region failover setup** using Route 53.
- Deployed an **active-active infrastructure** in a second AWS region.
- Implemented **RDS Multi-AZ** for automatic failover.

**Result:** Maintained **99.99% uptime**, reducing downtime from **4 hours to under 10 minutes**.

---

### **5. Application Memory Leak Causing Performance Issues**
**Situation:** A microservices-based application was consuming increasing memory, leading to **OutOfMemory (OOM) crashes**.

**Task:** Identify the memory leak and prevent future crashes.

**Action:**
- Used **Prometheus & Grafana** to analyze memory usage trends.
- Ran a **heap dump** and analyzed memory allocations.
- Found an **unreleased resource** in the application code.
- Implemented **garbage collection tuning** and memory profiling.

**Result:** Memory consumption **reduced by 40%**, eliminating crashes and improving stability.

---

### **6. High Latency in a Distributed System**
**Situation:** An API used by millions of users experienced **high latency** due to increased load.

**Task:** Optimize performance and reduce response times.

**Action:**
- Used **Jaeger (tracing)** to analyze request paths.
- Identified an **N+1 query problem** slowing database queries.
- Implemented **caching (Redis)** and optimized queries.
- Increased worker threads and enabled **CDN caching**.

**Result:** Response times improved from **5s to 200ms**, enhancing user experience.

---

### **7. CI/CD Pipeline Failing to Deploy**
**Situation:** A CI/CD pipeline was failing due to a broken deployment script.

**Task:** Fix the CI/CD pipeline and ensure reliable deployments.

**Action:**
- Debugged the logs in **GitHub Actions** and **Jenkins**.
- Identified missing dependencies in the build stage.
- Fixed the pipeline by adding proper dependency management.
- Implemented a **rollback mechanism** for failed deployments.

**Result:** Deployment success rate improved to **99%**, reducing release failures.

---

### **8. Security Breach: Unauthorized API Access**
**Situation:** A security vulnerability allowed unauthorized access to API endpoints.

**Task:** Fix the security hole and prevent future breaches.

**Action:**
- Used **AWS GuardDuty** and **CloudTrail** to trace unauthorized requests.
- Implemented **JWT authentication and API Gateway WAF rules**.
- Conducted **penetration testing** to identify more vulnerabilities.
- Enforced **IAM least privilege policies** for API access.

**Result:** No further security incidents, and compliance with **SOC2 and ISO27001** standards was strengthened.

---

### **9. DNS Misconfiguration Causing Website Downtime**
**Situation:** Users were unable to access a production website due to **DNS resolution issues**.

**Task:** Fix the DNS issue and restore accessibility.

**Action:**
- Used `nslookup` and `dig` to diagnose DNS propagation issues.
- Found an **incorrect CNAME record** causing failures.
- Corrected DNS settings and configured **Cloudflare for redundancy**.
- Implemented **DNS health checks** with automated alerts.

**Result:** Website downtime reduced from **2 hours to under 5 minutes**.

---
### **10️⃣ SSL Certificate Expiry**
**Situation:** A production API stopped working because an SSL certificate expired unexpectedly.

**Task:** Renew the SSL certificate and prevent future occurrences.

**Action:**
- Checked logs and found SSL expiration errors.
- Renewed the SSL certificate manually and updated it in AWS ACM.
- Implemented automated SSL renewal using Let's Encrypt and monitoring alerts.

**Result:** The API was restored within **15 minutes**, and automated renewal eliminated future manual interventions.

---

### **11️⃣ Disk Space Full on Database**
**Situation:** A production database crashed due to a lack of disk space.

**Task:** Free up space and prevent similar issues in the future.

**Action:**
- Used `df -h` and `du -sh` to identify space usage.
- Cleared unnecessary logs and optimized table indexes.
- Set up automatic disk monitoring and archival of old data.

**Result:** Disk usage reduced by **50%**, and alerts ensured proactive space management.

---

### **12️⃣ Log Flooding Impacting Performance**
**Situation:** A backend service was experiencing high CPU and memory usage due to excessive logging.

**Task:** Optimize logging to reduce resource consumption.

**Action:**
- Identified high log volume with `journalctl` and `fluentd`.
- Adjusted log levels to suppress unnecessary debug logs.
- Implemented centralized log management with Logstash and ELK.

**Result:** Log volume reduced by **70%**, improving system performance.

---

### **13️⃣ Helm Deployment Failure**
**Situation:** A Helm release failed, preventing a microservice from deploying.

**Task:** Troubleshoot and resolve the deployment issue.

**Action:**
- Used `helm list` and `helm status` to inspect the failed release.
- Found a misconfigured `values.yaml` file.
- Fixed the configuration and re-deployed with `helm upgrade`.

**Result:** The microservice deployed successfully, and a validation step was added to the CI/CD pipeline.

---

### **14️⃣ Unexpected Traffic Spike**
**Situation:** A sudden increase in traffic caused performance degradation.

**Task:** Scale the system to handle the increased load.

**Action:**
- Monitored traffic with AWS CloudWatch and Prometheus.
- Increased auto-scaling thresholds and added rate-limiting at the API Gateway.
- Optimized database queries and caching mechanisms.

**Result:** Application performance was restored, and future spikes were handled seamlessly.

---

### **15️⃣ Data Corruption in RDS**
**Situation:** A database table became corrupted due to a failed migration.

**Task:** Restore the database while minimizing downtime.

**Action:**
- Identified corruption using AWS RDS logs.
- Restored the last consistent snapshot and replayed recent transactions.
- Implemented a stricter database migration strategy.

**Result:** Data was recovered, and future corruptions were prevented with automated backup verification.

---

### **16️⃣ Cloud Cost Overages**
**Situation:** Monthly cloud bills exceeded the allocated budget.

**Task:** Reduce cloud costs while maintaining performance.

**Action:**
- Used AWS Cost Explorer to identify expensive resources.
- Implemented auto-scaling, spot instances, and storage lifecycle policies.
- Optimized workloads using serverless where applicable.

**Result:** Cloud costs reduced by **35%**, improving cost efficiency.

---

### **17️⃣ Incident Response Failure**
**Situation:** A production outage took too long to diagnose and resolve.

**Task:** Improve the incident response process.

**Action:**
- Implemented an on-call rotation with PagerDuty.
- Created runbooks for common incidents.
- Conducted post-mortem reviews to improve response strategies.

**Result:** Incident response time improved by **60%**, reducing downtime.

---

### **18️⃣ Single Point of Failure Risk**
**Situation:** A critical service was running without redundancy.

**Task:** Introduce high availability and failover mechanisms.

**Action:**
- Identified the service dependencies using dependency mapping.
- Implemented a multi-AZ and load-balanced architecture.
- Introduced failover using Route 53 and health checks.

**Result:** **99.99% uptime** achieved, eliminating single points of failure.

---

### **19️⃣ Slow CI/CD Pipelines**
**Situation:** CI/CD deployments were taking too long, delaying releases.

**Task:** Optimize the pipeline to reduce build times.

**Action:**
- Enabled caching for dependencies and Docker layers.
- Introduced parallel builds and test execution.
- Optimized artifacts by reducing unnecessary package installations.

**Result:** Deployment time reduced by **50%**, accelerating release cycles.

---

### **20️⃣ Microservices Network Latency**
**Situation:** Inter-service communication was slow, degrading performance.

**Task:** Improve microservices networking.

**Action:**
- Analyzed Istio service mesh logs for bottlenecks.
- Optimized request routing and reduced unnecessary cross-service calls.
- Introduced sidecar proxy optimizations.

**Result:** Latency reduced by **40%**, improving microservice efficiency.

---

### **21️⃣ RBAC Misconfiguration**
**Situation:** Developers had excessive permissions, posing a security risk.

**Task:** Implement proper role-based access control (RBAC).

**Action:**
- Audited IAM roles and Kubernetes RBAC permissions.
- Implemented least privilege policies and scoped API access.
- Conducted periodic security reviews and access audits.

**Result:** Security compliance improved, reducing risk of unauthorized access.

---

### **22️⃣ Unpatched Security Vulnerabilities**
**Situation:** A security scan revealed multiple unpatched vulnerabilities.

**Task:** Patch the vulnerabilities and improve security processes.

**Action:**
- Used Trivy and AWS Inspector to detect vulnerabilities.
- Implemented automated patching and dependency updates.
- Integrated security scanning into CI/CD pipelines.

**Result:** **100% compliance achieved**, preventing future vulnerabilities.

---

### **23️⃣ Excessive Storage Costs in S3**
**Situation:** S3 storage costs were unexpectedly high.

**Task:** Reduce storage costs without losing data.

**Action:**
- Identified infrequently accessed objects using S3 analytics.
- Implemented lifecycle rules to transition data to Glacier.
- Compressed and deduplicated logs before storage.

**Result:** S3 storage costs reduced by **45%**, improving cost efficiency.

---

### **24️⃣ Zombie Processes Consuming Resources**
**Situation:** A server had multiple zombie processes consuming CPU and memory.

**Task:** Identify and remove zombie processes.

**Action:**
- Used `ps aux` and `top` to locate zombie processes.
- Killed orphaned processes using `kill -9`.
- Automated process cleanup using a cron job.

**Result:** CPU and memory usage reduced, improving server efficiency.

---

### **25️⃣ Delayed Outage Detection**
**Situation:** System outages were not detected in time.

**Task:** Improve monitoring and alerting.

**Action:**
- Integrated Prometheus alerting with Slack and PagerDuty.
- Set up synthetic monitoring for early issue detection.
- Created dashboards for real-time observability.

**Result:** Outages detected within **1 minute**, reducing downtime significantly.

---

### **🚀 Final Thoughts**
These **real-world SRE scenarios** demonstrate how to handle incidents, optimize reliability, and enhance security. Let me know if you need more advanced cases! 🚀

Each of the remaining cases is expanded with a full STAR response, detailing the **Situation, Task, Action, and Result** for each scenario.

---
