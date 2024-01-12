# Well-Architected Framework

The AWS Well-Architected Framework helps you understand the pros and cons of decisions you make while building systems on AWS.
* learn architectural best practices for designing and operating reliable, secure, efficient, cost-effective and sustainable systems in the cloud.

* [AWS Well-Architected Tool](http://aws.amazon.com/well-architected-tool/?ref=wellarchitected-wp)

* [AWS Well-Architected Lab](https://www.wellarchitectedlabs.com/?ref=wellarchitected-wp)

### The pillars of the AWS Well-Architected Framework
* **Operational excellence**: The ability to support development and run workloads effectively, gain insight into their operations, and to continuously improve supporting processes and procedures to deliver business value.
* **Security**: The security pillar describes how to take advantage of cloud technologies to protect data, systems, and assets in a way that can improve your security posture.
* **Reliability**: The reliability pillar encompasses the ability of a workload to perform its intended function correctly and consistently when it’s expected to. 
  * This includes the ability to operate and test the workload through its total lifecycle. 
  * This paper provides in-depth, best practice guidance for implementing reliable workloads on AWS.
* **Performance efficiency**: The ability to use computing resources efficiently to meet system requirements, and to maintain that efficiency as demand changes and technologies evolve.
* **Cost optimization**: The ability to run systems to deliver business value at the lowest price point.
* **Sustainability**: The ability to continually improve sustainability impacts by reducing energy consumption and increasing efficiency across all components of a workload by maximizing the benefits from the provisioned resources and minimizing the total resources required.

### Terms of AWS Well-Architected Framework
* `Component`: The code, code, configuration, and AWS Resources that together deliver against a requirement.
  * A component is often the unit of technical ownership, and is decoupled from other components.
* `Workload`: is used to identify a set of components that together deliver business value.
  * A workload is usually the level of detail that business and technology leaders communicate about.
* `Architecture`: How components work together in a workload.
  * How components communicate and interact is often the focus of architecture diagrams.
* `Milestones`: mark key changes in your architecture as it evolves throughout the product lifecycle (design, implementation, testing, go live, and in production).
* `Technology portfolio`: The collection of workloads that are required for the business to operate.
* `Level of effort`: is categorizing the amount of time, effort, and complexity a task requires for implementation.
  * **High**: The work might take multiple weeks or multiple months. This could be broken out into multiple stories, releases, and tasks.
  * **Medium**: The work might take multiple days or multiple weeks. This could be broken out into multiple release and tasks.
  * **Low**: The work might take multiple hours or multiple days. This could be broken out into multiple tasks.


### General design principles

The Well-Architected Framework identifies a set of general design principles to facilitate good design in the cloud

* **Stop guessing your capacity needs**: If you make a poor capacity decision when deploying a workload, you might end up sitting on expensive idle resources or dealing with the performance implications of limited capacity. With cloud computing, these problems can go away.
  * You can use as much or as little capacity as you need, and scale up and down automatically.
* **Test systems at production scale**:  You can create a production-scale test environment on demand, complete your testing, and then decommission the resources.
  * You only pay for the test environment when it's running, you can simulate your live environment for a fraction of the cost of testing on premises.
* **Automate with architectural experimentation in mind**: Automation permits you to create and replicate your workloads at low cost and avoid the expense of manual effort. 
  * You can track changes to your automation, audit the impact, and revert to previous parameters when necessary.
* **Consider evolutionary architectures**: As a business and its context continue to evolve, these initial decisions might hinder the system's ability to deliver changing business requirements.
  * In the cloud, the capability to automate and test on demand lowers the risk of impact from design changes.
  * This permits systems to evolve over time so that businesses can take advantage of innovations as a standard practice.
* **Drive architectures using data**: In the cloud, you can collect data on how your architectural choices affect the behavior of your workload.
  * This lets you make fact-based decisions on how to improve your workload.
  * Your cloud infrastructure is code, so you can use that data to inform your architecture choices and improvements over time.
* **Improve through game days**: Test how your architecture and processes perform by regularly scheduling game days to simulate events in production.
  * This will help you understand where improvements can be made and can help develop organizational experience in dealing with events.