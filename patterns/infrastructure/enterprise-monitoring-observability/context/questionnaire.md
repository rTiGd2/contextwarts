# Enterprise Monitoring & Observability Pattern - Context Questionnaire

## Purpose
This questionnaire gathers the specific context needed to design and implement the optimal monitoring and observability stack for your system. Your answers help determine the right tools, configuration, and monitoring strategy for your specific environment and requirements.

---

## Quick Context Assessment (2 minutes)

### System Overview
1. **What type of system needs monitoring?**
   - [ ] Single web application
   - [ ] API service with database
   - [ ] Microservices architecture (3-10 services)
   - [ ] Large distributed system (10+ services)
   - [ ] Legacy monolith with multiple components
   - [ ] Multi-tenant SaaS platform

2. **Current monitoring state:**
   - [ ] No monitoring (need everything)
   - [ ] Basic server monitoring only
   - [ ] Application logs but no metrics
   - [ ] Some monitoring tools but incomplete
   - [ ] Good monitoring but need to enhance/standardize

3. **Primary monitoring goal:**
   - [ ] Prevent system downtime
   - [ ] Improve application performance
   - [ ] Meet compliance requirements
   - [ ] Enhance debugging and troubleshooting
   - [ ] Optimize infrastructure costs
   - [ ] All of the above

---

## Detailed Context (8-12 minutes)

### System Architecture and Scale

**4. System deployment environment:**
   - [ ] Single cloud provider (AWS, Azure, GCP)
   - [ ] Multi-cloud deployment
   - [ ] On-premise servers
   - [ ] Hybrid (cloud + on-premise)
   - [ ] Edge computing/distributed locations
   - [ ] Kubernetes/container orchestration
   - [ ] Serverless functions

**5. System scale and complexity:**
   - [ ] Small (1-5 services, <1K users)
   - [ ] Medium (5-20 services, 1K-100K users)
   - [ ] Large (20-100 services, 100K-1M users)
   - [ ] Enterprise (100+ services, 1M+ users)
   - [ ] Variable/seasonal traffic patterns

**6. Application architecture type:**
   - [ ] Traditional monolith
   - [ ] Modular monolith
   - [ ] Microservices
   - [ ] Event-driven architecture
   - [ ] Serverless/function-based
   - [ ] Mix of different architectures

### Team and Organizational Context

**7. Team size and expertise:**
   - [ ] Solo developer (need simple, automated solutions)
   - [ ] Small team 2-10 (prefer managed solutions)
   - [ ] Medium team 10-50 (can handle some complexity)
   - [ ] Large team 50+ (can implement complex solutions)
   - [ ] Multiple teams (need standardized approaches)

**8. Monitoring/DevOps expertise:**
   - [ ] Beginner (new to monitoring tools)
   - [ ] Some experience (used basic monitoring)
   - [ ] Experienced (familiar with Prometheus, Grafana)
   - [ ] Expert (deep monitoring and observability knowledge)
   - [ ] Mixed expertise across team

**9. Operational capacity:**
   - [ ] Minimal (want managed/automated solutions)
   - [ ] Standard (regular maintenance acceptable)
   - [ ] Dedicated (have DevOps/SRE team)
   - [ ] Enterprise (full monitoring operations team)

### Requirements and Constraints

**10. Performance monitoring needs:**
   - [ ] Basic uptime monitoring
   - [ ] Response time and throughput metrics
   - [ ] Deep application performance monitoring (APM)
   - [ ] User experience and business metrics
   - [ ] Database and infrastructure performance
   - [ ] Real-time alerting for critical issues

**11. Compliance and security requirements:**
   - [ ] No specific compliance needs
   - [ ] GDPR (data protection and privacy)
   - [ ] HIPAA (healthcare data security)
   - [ ] PCI-DSS (payment processing)
   - [ ] SOX (financial reporting)
   - [ ] Government/defense compliance
   - [ ] Industry-specific regulations

**12. Budget and tool preferences:**
   - [ ] Open source only (cost-conscious)
   - [ ] Primarily open source with some commercial tools
   - [ ] Mixed approach (best tool for each job)
   - [ ] Commercial solutions preferred (managed services)
   - [ ] Enterprise budget (best-in-class tools)

### Technical Requirements

**13. Data retention requirements:**
   - [ ] Short-term (days to weeks)
   - [ ] Medium-term (weeks to months)
   - [ ] Long-term (months to years)
   - [ ] Compliance-driven (specific requirements)
   - [ ] Variable by data type

**14. Integration requirements:** (Select all needed)
   - [ ] CI/CD pipeline integration
   - [ ] Incident management tools (PagerDuty, Opsgenie)
   - [ ] Communication tools (Slack, Microsoft Teams)
   - [ ] Ticketing systems (Jira, ServiceNow)
   - [ ] Business intelligence/analytics platforms
   - [ ] Security tools (SIEM, vulnerability scanners)
   - [ ] Cost management tools

**15. Alerting and notification preferences:**
   - [ ] Email notifications only
   - [ ] Multi-channel (email, Slack, SMS)
   - [ ] On-call rotation and escalation
   - [ ] Intelligent alerting (reduce noise)
   - [ ] Business hours vs after-hours policies
   - [ ] Mobile app notifications

---

## Monitoring-Specific Context (5-8 minutes)

### Current State Assessment

**16. Existing monitoring tools:** (Select all currently used)
   - [ ] None
   - [ ] Basic server monitoring (htop, basic alerts)
   - [ ] Application logs (but no centralized aggregation)
   - [ ] Cloud provider monitoring (CloudWatch, Azure Monitor)
   - [ ] Open source stack (Prometheus, Grafana)
   - [ ] Commercial APM (DataDog, New Relic, Dynatrace)
   - [ ] Custom monitoring solutions
   - [ ] ELK stack (Elasticsearch, Logstash, Kibana)

**17. Current monitoring gaps:** (Select all that apply)
   - [ ] No application performance monitoring
   - [ ] No centralized log aggregation
   - [ ] No distributed tracing for microservices
   - [ ] No business/user metrics
   - [ ] No automated alerting
   - [ ] No historical trend analysis
   - [ ] No infrastructure cost monitoring
   - [ ] No security event monitoring

### Specific Monitoring Needs

**18. Application monitoring priorities:** (Rank top 3)
   - [ ] Error rates and exception tracking
   - [ ] Response time and latency monitoring
   - [ ] Throughput and traffic patterns
   - [ ] Database query performance
   - [ ] Third-party API dependency monitoring
   - [ ] User experience and journey tracking
   - [ ] Business metrics and conversion rates
   - [ ] Resource utilization (CPU, memory, disk)

**19. Infrastructure monitoring needs:** (Select all required)
   - [ ] Server/VM resource monitoring
   - [ ] Container and Kubernetes monitoring
   - [ ] Network performance and connectivity
   - [ ] Database performance and availability
   - [ ] Load balancer and proxy monitoring
   - [ ] Storage and backup monitoring
   - [ ] Security and vulnerability monitoring
   - [ ] Cost and resource optimization

**20. Distributed system monitoring:** (If applicable)
   - [ ] Not applicable (monolithic system)
   - [ ] Service-to-service communication tracking
   - [ ] Distributed tracing across services
   - [ ] Service dependency mapping
   - [ ] Cross-service error correlation
   - [ ] Request flow visualization
   - [ ] Service mesh monitoring (if using Istio, Linkerd)

### Advanced Requirements

**21. Analytics and intelligence features:** (Select desired)
   - [ ] Anomaly detection and predictive alerting
   - [ ] Root cause analysis automation
   - [ ] Capacity planning and forecasting
   - [ ] Performance optimization recommendations
   - [ ] Business impact correlation
   - [ ] Machine learning-powered insights
   - [ ] Custom dashboard creation capabilities

**22. Enterprise features needed:** (Select if applicable)
   - [ ] Role-based access control
   - [ ] Multi-tenant monitoring (if SaaS)
   - [ ] API access for custom integrations
   - [ ] White-label dashboards for customers
   - [ ] Advanced data retention and archiving
   - [ ] High availability and disaster recovery
   - [ ] Professional support and SLAs

---

## Implementation Context (3-5 minutes)

### Timeline and Approach

**23. Implementation timeline:**
   - [ ] Urgent (need basic monitoring ASAP)
   - [ ] Standard (2-4 weeks for comprehensive setup)
   - [ ] Comprehensive (1-2 months for enterprise features)
   - [ ] Phased (start basic, enhance incrementally)

**24. Implementation approach preference:**
   - [ ] All-in-one solution (single vendor/platform)
   - [ ] Best-of-breed (choose best tool for each function)
   - [ ] Gradual migration (enhance existing tools)
   - [ ] Clean slate (replace everything)

**25. Deployment and hosting preferences:**
   - [ ] Fully managed SaaS solutions
   - [ ] Self-hosted open source tools
   - [ ] Hybrid (managed + self-hosted)
   - [ ] Cloud-native solutions
   - [ ] On-premise only (security/compliance)

### Success Criteria and Metrics

**26. Primary success metrics:** (Select top 3)
   - [ ] Reduced mean time to detection (MTTD)
   - [ ] Reduced mean time to resolution (MTTR)
   - [ ] Improved system uptime/availability
   - [ ] Better application performance
   - [ ] Reduced infrastructure costs
   - [ ] Enhanced developer productivity
   - [ ] Improved customer experience
   - [ ] Compliance audit success

**27. Acceptable complexity vs automation trade-off:**
   - [ ] Simple setup, less customization
   - [ ] Moderate complexity, good balance
   - [ ] High complexity, maximum customization
   - [ ] Fully automated, minimal manual intervention

---

## Additional Context

**28. Any specific monitoring tools you want to use or avoid?**
```
[Free text field for tool preferences and constraints]
```

**29. Current pain points with monitoring/troubleshooting:**
```
[Free text field for current challenges and problems]
```

**30. Any unique requirements or constraints not covered above?**
```
[Free text field for special requirements]
```

---

## Context Summary

Based on your responses, I'll provide:

1. **Recommended Monitoring Architecture** - Specific tools and configuration for your environment
2. **Implementation Roadmap** - Step-by-step approach considering your timeline and constraints
3. **Tool Selection Rationale** - Why specific tools are recommended for your context
4. **Configuration Guidelines** - Specific settings and best practices for your use case
5. **Integration Strategy** - How to integrate with your existing tools and workflows
6. **Success Metrics** - How to measure the effectiveness of your monitoring implementation

**Estimated Time to Complete Questionnaire: 15-20 minutes**
**Context Processing Time: 3-5 minutes**
**Detailed Recommendations Delivery: 10-15 minutes**