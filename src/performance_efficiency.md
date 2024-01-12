# Performance efficiency

The Performance Efficiency pillar includes the ability to use computing resources efficiently to meet system requirements, and to maintain that efficiency as demand changes and technologies evolve.

* [Efficiency Pillar whitepaper](https://docs.aws.amazon.com/wellarchitected/latest/performance-efficiency-pillar/welcome.html?ref=wellarchitected-wp)

### Design principles

* **Democratize advanced technologies**: Make advanced technology implementation smoother for your team by delegating complex tasks to your cloud vendor. Rather than asking your IT team to learn about hosting and running a new technology, consider consuming the technology as a service.
  * In the cloud, these technologies become services that your team can consume, permitting your team to focus on product development rather than resource provisioning and management.
* **Go global in minutes**: Deploying your workload in multiple AWS Regions around the world permits you to provide lower latency and a better experience for your customers at minimal cost.

* **Use serverless architectures**: Serverless architectures remove the need for you to run and maintain physical servers for traditional compute activities.
  * For example, serverless storage services can act as static websites (removing the need for web servers) and event services can host code.
  * This removes the operational burden of managing physical servers, and can lower transactional costs because managed services operate at cloud scale.
* **Experiment more often**:  With virtual and automatable resources, you can quickly carry out comparative testing using different types of instances, storage, or configurations.
* **Consider mechanical sympathy**: Understand how cloud services are consumed and always use the technology approach that aligns with your workload goals.
  * For example, consider data access patterns when you select database or storage approaches. 