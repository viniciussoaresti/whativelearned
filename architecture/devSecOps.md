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