# Operational excellence

The Operational Excellence pillar includes the ability to support development and run workloads effectively, gain insight into their operations, and to continuously improve supporting processes and procedures to deliver business value.

* [Operational Excellence Pillar whitepaper](https://docs.aws.amazon.com/wellarchitected/latest/operational-excellence-pillar/welcome.html)

### Design principles

* **Perform operations as code**: In the cloud, you can apply the same engineering discipline that you use for applications to your entire environment.
  * You can define your entire workload (applications infrastructure, etc.) as code and update it with code. 
  * You can script your operations procedures and automate their process by launching them in response to events.
  * By performing operations as code, you limit human error and create consistent responses to events.
* **Make frequent, small, reversible changes**: Design workloads that are scaleable and loosely coupled to permit components to be updated regularly.
  * Automated deployment techniques together with smaller, incremental changes reduces the blast radius and allows for faster reversal when failures occur.
  * This increases confidence to deliver beneficial changes to your workload while maintaining quality and adapting quickly to changes in market conditions.
* **Refine operations procedures frequently**:  As you evolve your workloads, evolve your operations appropriately.
  * As you use operations procedures, look for opportunities to improve them. 
  * Hold regular reviews and validate that all procedures are effective and that teams are familiar with them. 
  * Where gaps are identified, update procedures accordingly. 
  * Communicate procedural updates to all stakeholders and teams. 
* **Anticipate failure**: Perform “pre-mortem” exercises to identify potential sources of failure so that they can be removed or mitigated. 
  * Test your failure scenarios and validate your understanding of their impact. 
  * Test your response procedures to ensure they are effective and that teams are familiar with their process.
  * Set up regular game days to test workload and team responses to simulated events.
* **Learn from all operational failures**: Drive improvement through lessons learned from all operational events and failures. 
  * Share what is learned across teams and through the entire organization.
* **Use managed services**: Reduce operational burden by using AWS managed services where possible.
  * Build operational procedures around interactions with those services.
* **Implement observability for actionable insights**: Gain a comprehensive understanding of workload behavior, performance, reliability, cost, and health.
  * Establish key performance indicators (KPIs) and leverage observability telemetry to make informed decisions and take prompt action when business outcomes are at risk.
  * Proactively improve performance, reliability, and cost based on actionable observability data.  