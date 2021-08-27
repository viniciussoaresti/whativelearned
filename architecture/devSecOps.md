# DevSecOps:

## DevOps:

DevOps's a culture, which aims to get both development and operational teams closer.

The Dev team plans, creates, verifies, packages and releases an application, whereas the operation team is involved on the release, configuration, monitoring for the it and also on the planning for new ones.

## DevSecOps:

Comes to add to the security culture, and uniting DevOps with that, and provides methods for identifying security vulnerabilities (pre and post release) and why did they happen, and also for correcting them.

The development and release flow of DevOps is remodeled to:

- Plan:
Development and Operations teams, includes threat modeling;

- Code:
Development team, includes Static Source Code Analysis (SAST), Software Code Analysis and Open Source Software Governance;

- Build:
Development team, includes SAST and Dynamic Application Security Testing (DAST);

- Test:
Development team, includes Penetration Testing and Interactive Application Security Testing (IAST);

- Release:
Development and Operations teams, includes Compliance Validation;

- Deploy:
Operations team, includes Threat Intelligence;

- Operate:
Operations team, includes Red Team, SAST, DAST and IAST;

- Monitor:
Development and Operations teams, includes Crowdsourced Security Program;

### Why:

Cloud Security Top 10, [Sans](https://www.sans.org/):

- 1: Insecure Use of Developer Credentials:
Like a password stored on github.

- 2: Publicly Accessible Storage:
Data that should not be public.

- 3: Improper Use of Default Configurations:
Can introduce risk;

- 4: Broken Access Control:
Least privilege principles not followed.

- 5: Misconfigured Network Construct:
Not using methods do control network access beyond simple IP address-based rules.

- 6: Inadequate Monitoring and Logging:
Not considering a risk-based logging strategy.

- 7: Lack of Inventory Management:
Not considering strategies to enrich your environment with additional information around ownership, use-case and sensitivity.

- 8: Domain Hijacking:
Not reviewing the DNS and cloud configurations to prevent take-over situations.

- 9: Lack of a Disaster Recovery Plan:
Not having it is a real problem, as cloud environments do not automatically solve disaster recovery concerns.

- 10: Manual Account Configuration:
Doing things by hand limits your ability to scale and leverage cloud-native security tools and controls.

### How to (mostly tips on cloud development):

#### CALMS Framework:

- Culture:
Break down barriers between Development, Security and Operations through education and outreach;

- Automation:
Embed self-service automated security scanning and teting  in continuous delivery;

- Lean:
Value stream analysis of security and compliance processes to optimize flow;

- Measurement:
Use metrics to shape design and drive decisions;

- Share:
Share threats, risks and vulnerabilities, by adding them to engineering backlogs.

#### Pre-commit security activities:
- Threat Modeling/Attack Mapping:
Like evil user stories.

- Security & Privacy Stories:
Like OWASP ASVS.

- Manual and Peer Reviews:
Like on the github pull request, review board.

- Security Hooks:
Like git-hound and git-secrets.

- IDE Security Plugins:
Like DevSkim and Puma Scan.

- Secure Coding Standards:
Like CERT Secure Coding Standards and OWASP Proactive Controls.

#### Commit (Continuous Integration):
- Static Analysis:
Like Brakeman and ESLint.

- Kubernetes Security:
Like kube-audit and kube-hunter.

- Infrastructure as Code Analysis:
Like ansible-lint and Terrascan.

- Container Hardening:
Like Bane and CIS Benchmarks.

- Dependency Management:
Like Bundler-Audit and Github security alerts.

- Security Unit Tests:
Done for example on JUnit or Mocha.

- Container Security:
Like Actuary, Docker Bench and Falco.

#### Acceptance:
- Infrastructure as code:
Like Ansible and Vagrant.

- Security Testing:
Like Arachni and Cloud Container Attack Tool.

- Cloud Configuration Management:
Like AWS CloudFormation and Azure Resource Manager.

- Security Acceptance Testing:
Like BDD-Security and Gauntlt.

- Infrastructure Tests:
Like CIS and Terratest.

- Infrastructure Compliance Checks:
Like InSpec and Open Policy Agent.

- Vulnerability Management:
Like Archerysec and JackHammer.

#### Production:
- Security Smoke Tests:
Like ZAP Baseline Scan and Nmap.

- Cloud Secrets Management:
Like AWS KMS and Google Cloud KMS.

- Configuration Safety Checks:
Like AWS Config and Microsoft Azure Advisor.

- Cloud Security Testing:
Like CloudSploit and Nimbostratus.

- Secrets Management:
Like Ansible Vault and Chef Vault.

- Serverless Protection:
Like FunctionShield.

- Server Hardening:
Like CIS and dev-sec.io.

- Host Intrusion Detection System:
Like fail2ban and OSSEC.

#### Operations:
- Fault Injection:
Like Chaos Monkey and pumba.

- Cyber Simulations:
Like Game day exercises and tabletop scenarios.

- Blameless Postmortems:
Like Etsy Morgue.

- Cloud Monitoring:
Like AWS Security Hub and Google Cloud Security Command Center.

- Penetration Testing:
Like Attack-driven defense and red team exercises.

- Threat Intelligence:
Like Diamond Model and STIX.

- Cloud Compliance:
Like CIS AWS/Azure Benchmark and Netflix Repokid.

- Continuous Monitoring:
Like alerta and MozDef.

- Continuous Scanning:
Like Cloud Custodian and Netflix Aadvark.


## OWASP:

"The Open Web Application Security Project® (OWASP) is a nonprofit foundation that works to improve the security of software. Through community-led open-source software projects, hundreds of local chapters worldwide, tens of thousands of members, and leading educational and training conferences, the OWASP Foundation is the source for developers and technologists to secure the web", [OWASP](https://owasp.org/).

### OWASP Top 10 - 2017:

"The OWASP Top 10 focuses on identifying the most serious web application security risks for a broad array of organizations. For each of these risks, we provide generic information about likelihood and technical impact using the following simple ratings scheme, which is based on the OWASP Risk Rating Methodology", [OWASP](https://owasp.org/www-project-top-ten/2017/Application_Security_Risks).

- A1:2017-Injection:

"Injection flaws, such as SQL, NoSQL, OS, and LDAP injection, occur when untrusted data is sent to an interpreter as part of a command or query. The attacker’s hostile data can trick the interpreter into executing unintended commands or accessing data without proper authorization."

- A2:2017-Broken Authentication:

"Application functions related to authentication and session management are often implemented incorrectly, allowing attackers to compromise passwords, keys, or session tokens, or to exploit other implementation flaws to assume other users’ identities temporarily or permanently."

- A3:2017-Sensitive Data Exposure:

"Many web applications and APIs do not properly protect sensitive data, such as financial, healthcare, and PII. Attackers may steal or modify such weakly protected data to conduct credit card fraud, identity theft, or other crimes. Sensitive data may be compromised without extra protection, such as encryption at rest or in transit, and requires special precautions when exchanged with the browser."

- A4:2017-XML External Entities (XXE):

"Many older or poorly configured XML processors evaluate external entity references within XML documents. External entities can be used to disclose internal files using the file URI handler, internal file shares, internal port scanning, remote code execution, and denial of service attacks."

- A5:2017-Broken Access Control:

"Restrictions on what authenticated users are allowed to do are often not properly enforced. Attackers can exploit these flaws to access unauthorized functionality and/or data, such as access other users’ accounts, view sensitive files, modify other users’ data, change access rights, etc."

- Sensitive Data Exposure:

Stealing keys and executing man-in-the-middle attacks, for example.

- A6:2017-Security Misconfiguration:

"Security misconfiguration is the most commonly seen issue. This is commonly a result of insecure default configurations, incomplete or ad hoc configurations, open cloud storage, misconfigured HTTP headers, and verbose error messages containing sensitive information. Not only must all operating systems, frameworks, libraries, and applications be securely configured, but they must be patched/upgraded in a timely fashion."

- A7:2017-Cross-Site Scripting (XSS):

"XSS flaws occur whenever an application includes untrusted data in a new web page without proper validation or escaping, or updates an existing web page with user-supplied data using a browser API that can create HTML or JavaScript. XSS allows attackers to execute scripts in the victim’s browser which can hijack user sessions, deface web sites, or redirect the user to malicious sites."

- A8:2017-Insecure Deserialization:

"Insecure deserialization often leads to remote code execution. Even if deserialization flaws do not result in remote code execution, they can be used to perform attacks, including replay attacks, injection attacks, and privilege escalation attacks."

- A9:2017-Using Components with Known Vulnerabilities:

"Components, such as libraries, frameworks, and other software modules, run with the same privileges as the application. If a vulnerable component is exploited, such an attack can facilitate serious data loss or server takeover. Applications and APIs using components with known vulnerabilities may undermine application defenses and enable various attacks and impacts."

- A10:2017-Insufficient Logging & Monitoring:

"Insufficient logging and monitoring, coupled with missing or ineffective integration with incident response, allows attackers to further attack systems, maintain persistence, pivot to more systems, and tamper, extract, or destroy data. Most breach studies show time to detect a breach is over 200 days, typically detected by external parties rather than internal processes or monitoring."

## Examples:

- Many practical examples for patching some applications on [Globo's DevSecLabs](https://github.com/globocom/secDevLabs);
- Free, online web security training from the creators of Burp Suite on [Portswigger](https://portswigger.net/web-security);