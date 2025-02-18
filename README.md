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
