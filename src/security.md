# Security

The Security pillar encompasses the ability to protect data, systems, and assets to take advantage of cloud technologies to improve your security.

* [Security Pillar whitepaper](https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/welcome.html?ref=wellarchitected-wp)

### Design principles

* **Implement a strong identity foundation**: Implement the principle of least privilege and enforce separation of duties with appropriate authorization for each interaction with your AWS resources.
  * Centralize identity management, and aim to eliminate reliance on long-term static credentials.
* **Maintain traceability**: Monitor, alert, and audit actions and changes to your environment in real time.
  * Integrate log and metric collection with systems to automatically investigate and take action.
* **Apply security at all layers**: Apply a defense in depth approach with multiple security controls.
  * Apply to all layers (for example, edge of network, VPC, load balancing, every instance and compute service, operating system, application, and code).
* **Automate security best practices**: Automated software-based security mechanisms improve your ability to securely scale more rapidly and cost-effectively. 
   *  Create secure architectures, including the implementation of controls that are defined and managed as code in version-controlled templates.
* **Protect data in transit and at rest**: Classify your data into sensitivity levels and use mechanisms, such as encryption, tokenization, and access control where appropriate.
* **Keep people away from data**:  Use mechanisms and tools to reduce or eliminate the need for direct access or manual processing of data. 
  * This reduces the risk of mishandling or modification and human error when handling sensitive data.
* **Prepare for security events**: Prepare for an incident by having incident management and investigation policy and processes that align to your organizational requirements.
  * Run incident response simulations and use tools with automation to increase your speed for detection, investigation, and recovery.