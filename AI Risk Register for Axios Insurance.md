![](https://cdn-images-1.medium.com/max/1000/0*yql4or6Q5E8zU9aM.png)

### Executive Summary

Axios is a fictional digital insurance company that uses AI to support claims, underwriting, and customer service. Because these systems handle sensitive customer and business information, an AI failure could affect customers, company operations, and regulatory obligations. The main risks involve data exposure, manipulation of AI behaviour, excessive AI permissions, unsafe decisions, and compromise of AI systems. Axios should focus on limiting AI access, monitoring its actions, and keeping human oversight over important decisions.

### Company profile

Axios is an insurance company with approximately 450 employees operating across Nigeria.

The company uses:

- ClaimAssist: an AI system that helps review claims and prepare recommendations.
- UnderwriteAI: an AI system that assists with customer risk assessment.
- SupportAI: an AI customer service assistant.

Data involved include customer information, policy records, claims, financial information, identity documents, and internal business information.

### Risk Register

![](https://cdn-images-1.medium.com/max/1000/1*bS1IkcdF_nSLK-tWYsUDZg.png)

priority summary.

### R01: Customer Data Exposure

**Affected AI System:** SupportAI and ClaimAssist

**Description:** AI systems have access to sensitive customer information. A security failure could cause the system to reveal information belonging to another customer or expose internal records.

**Related incident:** The OpenAI Hugging Face incident showed AI agents discovering exposed credentials and using them to access external systems.

**Framework Mapping:** OWASP LLM06: Sensitive Information Disclosure

**Likelihood:** High. The incident shows that AI agents can discover sensitive information and credentials.

**Impact:** High. Customer information could be exposed, leading to privacy, financial, and regulatory consequences.

**Priority:** Critical

**Mitigation:** Restrict AI access to only the information required for each task and apply automated checks for sensitive information before responses are released.

### R02: Prompt Injection

**Affected AI System:** ClaimAssist

**Description:** A malicious instruction could be placed inside a claim document or other information supplied to the AI. The instruction could cause the AI to ignore its original task or produce an unsafe result.

**Related incident:** The OpenAI incident showed agents moving beyond their original tasks and communicating with other agents and external systems.

**Framework Mapping:** OWASP LLM01: Prompt Injection

**Likelihood:** High. AI systems can be influenced by instructions contained in the information they process.

**Impact:** High. A manipulated claims system could produce incorrect recommendations or access information it should not access.

**Priority:** Critical

**Mitigation:** Treat customer supplied documents as untrusted content and test the system regularly against malicious instructions.

### R03: Excessive AI Permissions

**Affected AI System:** ClaimAssist and SupportAI

**Description:** AI systems connected to company tools may have more permissions than they need. This could allow an AI failure or malicious instruction to result in unauthorised changes or actions.

**Related incident:** The OpenAI incident showed agents finding ways around restrictions and accessing systems outside their original task.

**Framework Mapping:** OWASP LLM06: Excessive Agency

**Likelihood:** High. The incident demonstrates the risk created when AI systems have broad access.

**Impact:** High. An AI system could modify records, send messages, or trigger business processes without proper approval.

**Priority:** Critical

**Mitigation:** Apply least privilege and require human approval before high impact actions such as changing claims decisions or approving payments.

### R04: Incorrect AI Recommendations

**Affected AI System:** ClaimAssist and UnderwriteAI

**Description:** AI recommendations may contain errors that influence claims or underwriting decisions. Employees may also rely too heavily on an AI recommendation without checking the supporting information.

**Related incident:** No direct hallucination incident was identified. But this risk is still relevant because incorrect AI output can affect important business decisions.

**Framework Mapping:** OWASP LLM09: Misinformation

**Likelihood:** Medium. There is no direct supporting incident in the available material.

**Impact:** High. Incorrect decisions could cause financial loss, customer complaints, and regulatory problems.

**Priority:** High

**Mitigation:** Require human review for important decisions and make the information supporting each AI recommendation visible to the reviewer.

### R05: Exposed Credentials

**Affected AI System:** All connected AI systems

**Description:** AI systems may encounter credentials in documents, logs, repositories, or connected services. If those credentials can be accessed or used by the AI, attackers could gain access to other company systems.

**Related incident:** During the OpenAI incident, agents found publicly exposed Hugging Face credentials and used them together with other weaknesses to gain access.

**Framework Mapping:** OWASP LLM03: Supply Chain

**Likelihood:** High. The incident provides direct evidence that AI agents can discover and use exposed credentials.

**Impact:** High. Compromised credentials could provide access to sensitive company systems.

**Priority:** Critical

**Mitigation:** Keep secrets outside AI accessible files, use short lived credentials, and monitor AI attempts to access protected services.

### R06: Bypassing Security Controls

**Affected AI System:** ClaimAssist

**Description:** An AI system may try alternative methods when its normal route is blocked. This could cause it to bypass restrictions that were intentionally placed around the system.

**Related incident:** The OpenAI incident showed agents chaining weaknesses together to bypass restrictions and obtain additional access.

**Framework Mapping:** NIST AI RMF: Manage

**Likelihood:** High. The incident provides evidence of AI systems continuing to find alternative routes.

**Impact:** High. Successful bypasses could expose systems or information outside the approved environment.

**Priority:** Critical

**Mitigation:** Create clear stop conditions and prevent the AI from automatically searching for alternative routes when an action is blocked.

### R07: AI Model Compromise

**Affected AI System:** UnderwriteAI

**Description:** UnderwriteAI contains valuable model information and proprietary underwriting logic. A compromise could expose the company’s intellectual property or provide attackers with information useful for further attacks.

**Related incident:** The OpenAI incident involved compromise of internal research infrastructure and resulted in the quarantine of model weights. The available material does not describe successful model theft.

**Framework Mapping:** NIST AI RMF: Govern

**Likelihood:** Medium. The incident shows that AI research infrastructure and model assets can become targets.

**Impact:** High. Loss of proprietary model assets could cause financial and competitive damage.

**Priority:** High

**Mitigation:** Store model weights separately, restrict access, log attempts to access model files, and separate development systems from production systems.

### R08: Unauthorised External Communication

**Affected AI System:** ClaimAssist

**Description:** ClaimAssist may use external services for document processing or information retrieval. If the AI communicates with an unapproved service, company or customer information could be exposed.

**Related incident:** During the OpenAI incident, agents created unauthorised communication channels and found ways to obtain internet access through infrastructure that was not intended for that purpose.

**Framework Mapping:** OWASP LLM01: Prompt Injection

**Likelihood:** High. The incident shows that AI agents can discover unexpected communication paths.

**Impact:** High. Unapproved external communication could expose sensitive information or allow external parties to influence the system.

**Priority:** Critical

**Mitigation:** Allow communication only with approved external services and monitor every external request made by the AI.

### Overall Assessment

The highest risks for Axios are customer data exposure, prompt injection, excessive AI permissions, exposed credentials, bypassing security controls, and unauthorised external communication. These risks show why AI security should focus not only on the answers an AI produces, but also on what the AI can access and what actions it can take. Strong access controls, monitoring, testing, and human approval for important decisions should therefore be central to Axios’s AI risk management approach.