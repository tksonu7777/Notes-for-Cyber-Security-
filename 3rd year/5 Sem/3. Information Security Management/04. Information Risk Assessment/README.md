 
**Unit 4: Information Risk Assessment**

This unit focuses on the systematic process of identifying, analyzing, and evaluating risks to information assets, and then developing appropriate mitigation strategies.  A well-executed risk assessment is crucial for protecting sensitive data, maintaining operational efficiency, and complying with legal and regulatory requirements.

**4.1 Risk Assessment Concepts**

*   **Definition of Risk:** Risk, in the context of information security, is the potential for loss or damage resulting from a threat exploiting a vulnerability. It's not just about the *probability* of something happening, but also the *impact* if it does.

*   **Key Elements of Risk:**
    *   **Asset:**  Something of value that needs protection (e.g., data, systems, applications, hardware, physical facilities, people, reputation).
    *   **Threat:**  Any circumstance or event with the potential to cause harm (e.g., malware, hackers, natural disasters, human error, insider threats).
    *   **Vulnerability:** A weakness or flaw in an asset that can be exploited by a threat (e.g., unpatched software, weak passwords, lack of physical security, inadequate training).
    *   **Consequence/Impact:** The negative outcome or damage that occurs if a threat successfully exploits a vulnerability (e.g., data breach, financial loss, reputational damage, legal penalties, business disruption).
    *   **Likelihood/Probability:**  The chance that a particular threat will exploit a particular vulnerability.

*   **Purpose of Risk Assessment:**
    *   Identify and prioritize information security risks.
    *   Provide a basis for informed decision-making about security investments.
    *   Meet regulatory and legal requirements.
    *   Improve the overall security posture of the organization.
    *   Support business objectives by minimizing potential disruptions.
    *   Communicate risk to stakeholders in a clear and understandable manner.

*   **Types of Risk Assessment:**
    *   **Qualitative:**  Uses descriptive scales (e.g., low, medium, high) to assess likelihood and impact. Subjective and relies on expert opinion.
    *   **Quantitative:** Uses numerical values (e.g., monetary amounts, percentages) to measure likelihood and impact. More objective but requires more data and can be more complex.
    *   **Semi-Quantitative:**  A hybrid approach that combines qualitative and quantitative elements. Assigns numerical values to qualitative ratings.

*   **Risk Appetite/Tolerance:**  The level of risk that an organization is willing to accept.  This is a crucial consideration when deciding how to address identified risks.

*   **Risk Assessment Frameworks:** (These provide structured approaches to risk assessment)
    *   **NIST Risk Management Framework (RMF):** A comprehensive framework developed by the National Institute of Standards and Technology (NIST) in the U.S.
    *   **ISO 27005:**  An international standard providing guidelines for information security risk management.
    *   **OCTAVE (Operationally Critical Threat, Asset, and Vulnerability Evaluation):** A risk assessment methodology developed by Carnegie Mellon University.
    *   **FAIR (Factor Analysis of Information Risk):** A quantitative risk analysis methodology.

**4.2 System Assessment Approaches**

This section focuses on how to evaluate the security of specific systems within the organization. It involves a range of techniques to identify vulnerabilities and weaknesses.

*   **Vulnerability Scanning:**
    *   **Definition:** Automated process of identifying known vulnerabilities in systems and applications.
    *   **Tools:** Nessus, OpenVAS, Qualys, Nexpose.
    *   **How it works:** Scanners use databases of known vulnerabilities to check systems for missing patches, misconfigurations, and other weaknesses.
    *   **Benefits:** Relatively quick and easy to perform, provides a broad overview of vulnerabilities.
    *   **Limitations:** Can generate false positives, may not identify all vulnerabilities (especially zero-day exploits), requires regular updates to vulnerability databases.

*   **Penetration Testing (Ethical Hacking):**
    *   **Definition:** Simulated attack on a system or network to identify vulnerabilities that could be exploited by malicious actors.
    *   **Types:**
        *   **Black Box:** Tester has no prior knowledge of the system.
        *   **White Box:** Tester has full knowledge of the system (source code, architecture, etc.).
        *   **Grey Box:** Tester has partial knowledge of the system.
    *   **Process:** Reconnaissance, scanning, gaining access, maintaining access, covering tracks, reporting.
    *   **Benefits:** More thorough than vulnerability scanning, identifies exploitable vulnerabilities, provides a realistic assessment of security posture.
    *   **Limitations:** More time-consuming and expensive than vulnerability scanning, requires skilled testers, potential for disruption if not performed carefully.

*   **Security Audits:**
    *   **Definition:**  Formal review of security controls and practices to ensure compliance with policies, standards, and regulations.
    *   **Types:** Internal audits, external audits (e.g., SOC 2, ISO 27001).
    *   **Focus:** Reviewing documentation, interviewing personnel, testing controls, and verifying compliance.
    *   **Benefits:** Provides an independent assessment of security posture, identifies weaknesses in controls, helps ensure compliance.
    *   **Limitations:** Can be costly and time-consuming, may not identify all vulnerabilities, relies on the auditor's expertise.

*   **Security Configuration Reviews:**
    *   **Definition:** Examining the configuration settings of systems and applications to identify misconfigurations that could create vulnerabilities.
    *   **Tools:** Configuration management tools, scripting languages.
    *   **Focus:** Checking for weak passwords, default settings, unnecessary services, and other misconfigurations.
    *   **Benefits:** Relatively easy to perform, can identify common misconfigurations, improves the overall security posture.
    *   **Limitations:** Requires knowledge of system and application configurations, can be time-consuming.

*   **Code Review:**
    *   **Definition:** Examining source code for security vulnerabilities, coding errors, and other potential issues.
    *   **Types:** Manual code review, automated code analysis.
    *   **Focus:** Identifying buffer overflows, SQL injection vulnerabilities, cross-site scripting vulnerabilities, and other common coding errors.
    *   **Benefits:** Identifies vulnerabilities early in the development process, improves the quality and security of code.
    *   **Limitations:** Requires skilled developers with security expertise, can be time-consuming.

**4.3 Asset Identification**

This critical step involves identifying and cataloging all assets that are relevant to the organization's information security. Accurate asset identification is fundamental to understanding what needs to be protected.

*   **Definition of an Asset:** Anything of value to the organization. This includes tangible and intangible assets.

*   **Types of Assets:**
    *   **Information Assets:** Data, databases, documents, files, intellectual property.
    *   **Software Assets:** Operating systems, applications, utilities, source code.
    *   **Hardware Assets:** Servers, workstations, laptops, mobile devices, network devices, storage devices, physical infrastructure.
    *   **Physical Assets:** Buildings, facilities, equipment.
    *   **Human Assets:** Personnel, skills, knowledge.
    *   **Service Assets:** Cloud services, third-party services, utilities.
    *   **Reputational Assets:** Brand image, customer trust, public perception.

*   **Asset Attributes:** For each asset, you should document important attributes:
    *   **Asset Name/Description:** Clear and concise identifier.
    *   **Asset Owner:** The individual or team responsible for the asset.  Accountability is key.
    *   **Asset Custodian:** The individual or team responsible for the day-to-day management and security of the asset.
    *   **Asset Location:** Physical and/or logical location.
    *   **Asset Value:**  The importance of the asset to the organization (e.g., high, medium, low).  Consider confidentiality, integrity, and availability.
    *   **Asset Classification:**  The sensitivity level of the data stored or processed by the asset (e.g., confidential, internal use only, public).
    *   **Asset Dependencies:**  Other assets that the asset relies on.
    *   **Asset Security Requirements:**  Specific security controls required to protect the asset.
    *   **Asset Lifecycle Stage:**  Where the asset is in its lifecycle (e.g., acquisition, development, implementation, maintenance, disposal).

*   **Asset Inventory:**  A comprehensive list of all identified assets and their attributes.  This can be maintained in a spreadsheet, database, or specialized asset management tool.

*   **Importance of Asset Identification:**
    *   Provides a clear understanding of what needs to be protected.
    *   Enables accurate risk assessment.
    *   Facilitates the implementation of appropriate security controls.
    *   Supports incident response and recovery efforts.
    *   Helps ensure compliance with regulations.

**4.4 Threat Identification**

Threat identification is the process of identifying potential sources of harm to the organization's assets.

*   **Definition of a Threat:** Any circumstance or event with the potential to cause harm to an asset.

*   **Types of Threats:**
    *   **Malware:** Viruses, worms, Trojans, ransomware, spyware.
    *   **Hackers:** External attackers who attempt to gain unauthorized access to systems or data.
    *   **Insider Threats:** Employees, contractors, or other trusted individuals who intentionally or unintentionally cause harm.
    *   **Social Engineering:** Manipulating individuals into divulging confidential information or performing actions that compromise security.
    *   **Phishing:**  A type of social engineering that uses deceptive emails or websites to trick individuals into providing sensitive information.
    *   **Denial of Service (DoS) / Distributed Denial of Service (DDoS) Attacks:**  Overwhelming a system with traffic to make it unavailable to legitimate users.
    *   **Data Breaches:** Unauthorized access to or disclosure of sensitive data.
    *   **Physical Threats:** Natural disasters (e.g., floods, earthquakes, fires), theft, vandalism.
    *   **Human Error:** Accidental deletion of data, misconfiguration of systems, failure to follow security procedures.
    *   **Supply Chain Attacks:**  Compromising a vendor or supplier to gain access to the organization's systems or data.
    *   **Zero-Day Exploits:**  Attacks that exploit vulnerabilities that are unknown to the vendor and for which no patch is available.

*   **Threat Sources:**
    *   **External Actors:** Hackers, organized crime groups, nation-states, competitors.
    *   **Internal Actors:** Employees, contractors, vendors.
    *   **Natural Events:** Disasters, weather events.
    *   **System Failures:** Hardware failures, software bugs.

*   **Threat Intelligence:**  Information about current and emerging threats. This can be obtained from security vendors, government agencies, industry groups, and open-source intelligence sources.

*   **Threat Modeling:** A structured approach to identifying and analyzing threats to a specific system or application. This involves identifying potential attack vectors, vulnerabilities, and the impact of a successful attack.

*   **Importance of Threat Identification:**
    *   Provides a clear understanding of the potential threats that the organization faces.
    *   Enables the development of appropriate security controls to mitigate those threats.
    *   Supports proactive security measures.
    *   Helps prioritize security investments.

**4.5 Control Identification**

This involves identifying the security controls that are in place or that could be implemented to mitigate identified risks.

*   **Definition of a Control:**  A safeguard or countermeasure that reduces the likelihood or impact of a threat exploiting a vulnerability.

*   **Types of Controls:**
    *   **Technical Controls:** Implemented using technology (e.g., firewalls, intrusion detection systems, antivirus software, access control lists, encryption).
    *   **Administrative Controls:** Policies, procedures, standards, and guidelines (e.g., security awareness training, background checks, incident response plans, change management processes).
    *   **Physical Controls:** Physical barriers and security measures (e.g., locks, fences, security guards, surveillance cameras, environmental controls).
    *   **Preventive Controls:** Designed to prevent incidents from occurring (e.g., firewalls, access control lists, security awareness training).
    *   **Detective Controls:** Designed to detect incidents that have already occurred (e.g., intrusion detection systems, audit logs, security monitoring).
    *   **Corrective Controls:** Designed to restore systems to a normal state after an incident (e.g., incident response plans, backup and recovery procedures).
    *   **Compensating Controls:** Alternative controls that are implemented when a primary control is not feasible (e.g., implementing strong authentication for a system that cannot be patched).

*   **Control Objectives:**  Specific security goals that controls are designed to achieve (e.g., protect the confidentiality of data, prevent unauthorized access to systems, ensure the availability of critical services).

*   **Control Frameworks:**  Sets of controls that are designed to address specific security risks or compliance requirements (e.g., NIST Cybersecurity Framework, ISO 27001, COBIT).

*   **Sources of Information for Control Identification:**
    *   Security policies and procedures
    *   Security standards and guidelines
    *   Control frameworks
    *   Industry best practices
    *   Security vendor recommendations
    *   Expert opinion

*   **Importance of Control Identification:**
    *   Provides a clear understanding of the security controls that are in place.
    *   Identifies gaps in security controls.
    *   Enables the development of a comprehensive security plan.
    *   Supports compliance with regulations.

**4.6 Vulnerability Identification**

This involves identifying weaknesses or flaws in assets that could be exploited by threats.

*   **Definition of a Vulnerability:**  A weakness or flaw in a system, application, or process that can be exploited by a threat.

*   **Types of Vulnerabilities:**
    *   **Software Vulnerabilities:** Bugs, coding errors, misconfigurations in software applications.
    *   **Hardware Vulnerabilities:** Flaws in hardware design or implementation.
    *   **Network Vulnerabilities:** Misconfigurations in network devices, weak protocols, lack of encryption.
    *   **Physical Vulnerabilities:** Weaknesses in physical security controls, such as inadequate locks or surveillance.
    *   **Human Vulnerabilities:** Lack of security awareness, weak passwords, social engineering susceptibility.
    *   **Configuration Vulnerabilities:**  Misconfigured systems, default passwords, unnecessary services enabled.

*   **Vulnerability Assessment Techniques:**
    *   **Vulnerability Scanning:**  Automated process of identifying known vulnerabilities in systems and applications (discussed in 4.2).
    *   **Penetration Testing:**  Simulated attack on a system or network to identify exploitable vulnerabilities (discussed in 4.2).
    *   **Code Review:**  Examining source code for security vulnerabilities (discussed in 4.2).
    *   **Security Configuration Reviews:** Examining the configuration settings of systems and applications (discussed in 4.2).
    *   **Security Audits:**  Formal review of security controls and practices (discussed in 4.2).
    *   **Manual Inspection:** Manually reviewing systems and applications for vulnerabilities.

*   **Vulnerability Databases:**  Databases of known vulnerabilities, such as the National Vulnerability Database (NVD) and the Common Vulnerabilities and Exposures (CVE) list.

*   **Importance of Vulnerability Identification:**
    *   Provides a clear understanding of the weaknesses in assets.
    *   Enables the prioritization of remediation efforts.
    *   Reduces the likelihood of successful attacks.
    *   Supports compliance with regulations.

**4.7 Consequences Identification**

This step focuses on determining the potential negative outcomes or impacts that could result if a threat successfully exploits a vulnerability.

*   **Definition of Consequence/Impact:** The negative outcome or damage that occurs if a threat successfully exploits a vulnerability.

*   **Types of Consequences:**
    *   **Financial Loss:** Loss of revenue, fines, legal fees, costs of recovery.
    *   **Reputational Damage:** Loss of customer trust, damage to brand image, negative publicity.
    *   **Operational Disruption:** Interruption of business processes, loss of productivity.
    *   **Legal and Regulatory Penalties:** Fines, sanctions, lawsuits.
    *   **Data Breach:** Unauthorized access to or disclosure of sensitive data.
    *   **Loss of Intellectual Property:** Theft of trade secrets, patents, copyrights.
    *   **Physical Damage:** Damage to facilities, equipment, or infrastructure.
    *   **Harm to Individuals:** Injury or death to employees, customers, or the public.

*   **Factors to Consider When Assessing Consequences:**
    *   **The value of the asset that is compromised.**
    *   **The sensitivity of the data that is exposed.**
    *   **The criticality of the system or application that is affected.**
    *   **The duration of the disruption.**
    *   **The number of people who are affected.**
    *   **The legal and regulatory requirements that are applicable.**

*   **Qualitative vs. Quantitative Consequence Assessment:**
    *   **Qualitative:**  Uses descriptive scales (e.g., low, medium, high) to assess the severity of the consequences.
    *   **Quantitative:** Uses numerical values (e.g., monetary amounts) to measure the impact of the consequences.

*   **Importance of Consequences Identification:**
    *   Provides a clear understanding of the potential impact of security incidents.
    *   Enables the prioritization of risks.
    *   Supports the development of effective mitigation strategies.
    *   Helps justify security investments.

**4.8 Risk Analysis**

Risk analysis is the process of combining the likelihood of a threat exploiting a vulnerability with the potential consequences to determine the level of risk.

*   **Risk Calculation:**  The most common way to calculate risk is:

    **Risk = Likelihood x Impact**

    The specific scales used to measure likelihood and impact will vary depending on the risk assessment methodology.

*   **Qualitative Risk Analysis:**
    *   Uses descriptive scales to assess likelihood and impact.
    *   Example:
        *   Likelihood: Low, Medium, High
        *   Impact: Low, Medium, High
    *   Risk Matrix: A tool used to visualize the level of risk based on the likelihood and impact ratings.

*   **Quantitative Risk Analysis:**
    *   Uses numerical values to measure likelihood and impact.
    *   Example:
        *   Likelihood: Probability of occurrence (e.g., 0.1 = 10% chance)
        *   Impact: Monetary value of potential losses (e.g., $100,000)
    *   Annualized Loss Expectancy (ALE): A common metric used in quantitative risk analysis.

        **ALE = Single Loss Expectancy (SLE) x Annualized Rate of Occurrence (ARO)**

        *   **SLE:** The expected financial loss from a single occurrence of a risk event.
        *   **ARO:** The estimated number of times a risk event is expected to occur in a year.

*   **Semi-Quantitative Risk Analysis:**
    *   A hybrid approach that combines qualitative and quantitative elements.
    *   Assigns numerical values to qualitative ratings.
    *   Example:
        *   Likelihood: Low (1), Medium (5), High (10)
        *   Impact: Low (1), Medium (5), High (10)

*   **Tools and Techniques for Risk Analysis:**
    *   Risk matrices
    *   Decision trees
    *   Fault tree analysis
    *   Event tree analysis
    *   Monte Carlo simulation

*   **Importance of Risk Analysis:**
    *   Provides a clear understanding of the level of risk associated with each identified threat and vulnerability.
    *   Enables the prioritization of risks.
    *   Supports the development of effective risk treatment strategies.
    *   Helps justify security investments.

**4.9 Risk Evaluation**

Risk evaluation is the process of comparing the results of the risk analysis with the organization's risk criteria to determine whether the risk is acceptable or unacceptable.

*   **Risk Criteria:** The levels of risk that the organization is willing to accept. These are based on the organization's risk appetite and tolerance.

*   **Risk Acceptance:**  Deciding to accept a risk because the cost of mitigating it is too high or the risk is deemed to be low enough.
*   **Risk Tolerance:** The range of acceptable variation around a specific risk level.
*   **Risk Appetite:** The overall level of risk that an organization is willing to take.

*   **Risk Evaluation Process:**
    1.  Compare the calculated risk level with the organization's risk criteria.
    2.  Determine whether the risk is acceptable or unacceptable.
    3.  Document the decision and the rationale behind it.

*   **Factors to Consider When Evaluating Risk:**
    *   The potential impact of the risk on the organization's business objectives.
    *   The cost of mitigating the risk.
    *   The likelihood of the risk occurring.
    *   The organization's risk appetite and tolerance.
    *   Legal and regulatory requirements.
    *   Stakeholder expectations.

*   **Importance of Risk Evaluation:**
    *   Provides a basis for making informed decisions about risk treatment.
    *   Ensures that risks are managed in accordance with the organization's risk appetite.
    *   Supports compliance with regulations.

**4.10 Risk Treatment**

Risk treatment involves selecting and implementing appropriate measures to modify risks that are deemed unacceptable.  It's about deciding what to do with the risks you've identified and evaluated.

*   **Risk Treatment Options:**

    *   **Risk Avoidance:** Eliminating the risk by avoiding the activity or asset that is exposed to the risk.  (e.g., discontinuing a service, not using a particular technology).
    *   **Risk Transfer:** Transferring the risk to another party, such as an insurance company or a third-party service provider. (e.g., purchasing cyber insurance, outsourcing security functions).  Note that this transfers the *financial* risk, not necessarily the overall responsibility.
    *   **Risk Mitigation:** Reducing the likelihood or impact of the risk by implementing security controls.  This is the most common approach. (e.g., implementing firewalls, patching systems, providing security awareness training).
    *   **Risk Acceptance:** Accepting the risk because the cost of mitigating it is too high or the risk is deemed to be low enough (as discussed in Risk Evaluation).

*   **Selecting Risk Treatment Options:**
    *   Consider the cost and effectiveness of each treatment option.
    *   Balance the cost of treatment with the benefits of reducing the risk.
    *   Consider the organization's risk appetite and tolerance.
    *   Consider legal and regulatory requirements.
    *   Consult with stakeholders.

*   **Risk Treatment Plan:** A document that outlines the chosen risk treatment options and the steps that will be taken to implement them.  This should include:
    *   The identified risk
    *   The selected treatment option(s)
    *   The responsible parties
    *   The implementation timeline
    *   The expected outcomes
    *   The metrics that will be used to measure the effectiveness of the treatment

*   **Implementing Risk Treatment:**
    *   Implement the selected risk treatment options according to the risk treatment plan.
    *   Monitor the effectiveness of the treatment.
    *   Make adjustments as needed.

*   **Importance of Risk Treatment:**
    *   Reduces the likelihood and impact of security incidents.
    *   Protects the organization's assets.
    *   Supports the achievement of business objectives.
    *   Ensures compliance with regulations.

**4.11 Risk Assessment Documentation & Continuous Improvement**

This involves documenting the entire risk assessment process and ensuring that it is regularly reviewed and updated.

*   **Risk Assessment Report:** A comprehensive document that summarizes the findings of the risk assessment.  This should include:
    *   Scope and objectives of the risk assessment
    *   Methodology used
    *   Identified assets, threats, and vulnerabilities
    *   Calculated risk levels
    *   Recommended risk treatment options
    *   Risk treatment plan
    *   Assumptions and limitations

*   **Continuous Improvement:**
    *   Regularly review and update the risk assessment.  At least annually, but more frequently if there are significant changes to the organization's business environment, technology, or regulatory requirements.
    *   Monitor the effectiveness of risk treatment options.
    *   Identify and address any gaps in the risk assessment process.
    *   Solicit feedback from stakeholders.
    *   Use the results of the risk assessment to improve the organization's overall security posture.

*   **Importance of Risk Assessment Documentation & Continuous Improvement:**
    *   Provides a record of the risk assessment process.
    *   Facilitates communication about risks to stakeholders.
    *   Supports ongoing risk management efforts.
    *   Ensures that the risk assessment remains relevant and effective.
    *   Demonstrates due diligence to regulators and auditors.

**Key Takeaways**

*   **Risk assessment is a continuous process, not a one-time event.** It must be regularly reviewed and updated to reflect changes in the organization's environment, technology, and threat landscape.
*   **Effective risk assessment requires collaboration and communication among stakeholders.**  This includes IT staff, business managers, legal counsel, and other relevant parties.
*   **Risk assessment should be aligned with the organization's business objectives.**  The goal is to protect the organization's assets and support the achievement of its goals.
*   **There is no one-size-fits-all approach to risk assessment.** The methodology and tools used will vary depending on the organization's size, complexity, and industry.




---
---

### **Differences Between Risk Analysis, Risk Evaluation, Risk Treatment, and Risk Assessment**

| **Aspect**            | **Risk Analysis** | **Risk Evaluation** | **Risk Treatment** | **Risk Assessment** |
|----------------------|----------------|----------------|----------------|----------------|
| **Definition** | Identifying and measuring risks based on likelihood and impact. | Comparing analyzed risks against risk tolerance levels to prioritize actions. | Implementing strategies to mitigate, avoid, transfer, or accept risks. | The overall process of identifying, analyzing, evaluating, and treating risks. |
| **Purpose** | Understand potential risks and their impact. | Determine which risks need treatment and prioritize actions. | Select and apply appropriate measures to manage risks. | Provide a structured approach to identifying and handling risks. |
| **Key Activities** | - Identify threats, vulnerabilities, and consequences.  <br> - Calculate risk using formulas or qualitative methods.  <br> - Assess probability and impact of risks. | - Compare risks with acceptable risk thresholds.  <br> - Use risk matrices or cost-benefit analysis.  <br> - Categorize risks as high, medium, or low. | - Choose a risk management strategy (mitigation, transfer, avoidance, acceptance).  <br> - Implement security controls and policies.  <br> - Monitor risk reduction effectiveness. | - Identify assets, threats, and vulnerabilities.  <br> - Perform risk analysis and evaluation.  <br> - Define and apply risk treatment strategies.  <br> - Continuously review risk management processes. |
| **Key Output** | A detailed risk analysis report showing impact and likelihood. | Risk prioritization and ranking based on impact and tolerance. | Action plans, security measures, and risk mitigation strategies. | A complete risk management plan, including all assessment phases. |
| **Scope** | Focuses on analyzing risks in detail. | Focuses on deciding which risks need action. | Focuses on applying risk management strategies. | Covers the entire risk management lifecycle. |
| **Example** | Assessing the impact of a cyber-attack on customer data. | Determining whether a cyber-attack risk is acceptable or requires action. | Deploying firewalls, encryption, and cybersecurity training. | Performing an organization-wide security risk assessment. |

### **Summary**
- **Risk Analysis** → Identifies and measures risks.
- **Risk Evaluation** → Compares risks with thresholds to determine necessary actions.
- **Risk Treatment** → Applies strategies to reduce or manage risks.
- **Risk Assessment** → Encompasses the entire process, including analysis, evaluation, and treatment.

 















 
