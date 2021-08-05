# Privacy and Security by Design:

Course offered by Instituto Atlântico, discussing about privacy, LGPD, security and programming techniques.

## Privacy by Design:

First of all, since around 2016, a lot of discussions about personal data privacy are taking place in the world, producing, as a result, privacy laws, such as GDPR (EU), CCPA (California) and LGPD (Brazil).

There's been a lot of system attacks, including ransomware cases, and they're even worse in this pandemic context we're living (2020-2021). So there's even more focus to this topic than it already had, specially when we're talking about designing new components and systems. So we should, by design (not only on our implementation), protect the user's privacy.

Even earlier, Ann Cavoukian thought about privacy, and created the metodology we're talking about (Privacy by Design). In 2009 she formalized seven great principles to follow, which were made popular when adopted by the International Assembly of Privacy Comissioners and Data Protection Authorities in 2010, and since when it became a reference regarding many discussions regarding the GDPR, in 2016.

- 1: Proactive not Reactive; Preventative not Remedial;
- 2: Privacy as the Default Setting;
- 3: Privacy Embedded into Design;
- 4: Full Functionality – Positive-Sum, not Zero-Sum;
- 5: End-to-End Security – Full Lifecycle Protection;
- 6: Visibility and Transparency – Keep it Open;
- 7: Respect for User Privacy – Keep it User-Centric;

They can be further explained by the very [International Association of Privacy Professionals (IAPP) - (open page 6 for a TL;DR)](https://iapp.org/media/pdf/resource_center/pbd_implement_7found_principles.pdf).

## LGPD:

In our case (Brazil), all people, as well as all companies (public or private), are under the law's jurisdiction.

Then law protects all the people that are or could be identified by the data stored in the database. This

Users should be able to access, confirm treatment, correct, block, eliminate, revoke and port data.

Data should be stored anonymously where possible, and if something happens with their data, users should be notified, as well as reimbursed if something bad happens with it.

All data processing should be registered and there should be a report with the impacts of each data stored within the system.

Some of the principles of the LGPD are:

- Goal: "Why should this data be collected and processed?";
- Adequacy: "Is the collected data aligned with the app's purpose?";
- Need: "Am I using only the data I need?";
- Free access: "Can the user data be accessed easily by them?";
- Data Quality: "Are all the data exact and updated?";
- Transparency: "Are all processes regarding data use clear for the users?";
- Safety: "Are there administrative and technical measures to secure the data well?";
- Prevention: "Are there well-defined preventive methods to avoid accidents?";
- Non-Discrimination: "Could the data be used/is the data being used to discriminate the users?";
- Accountability: "Is the software (and its organization) informing the government regulators?";

### Actors:

Actors involved in all the process:

- User: Users which concede the data.
- Controller: Physical or juridical person that controls all decisions related to the form and purpose of personal data;
- Operator: Who handles the data process, ordered by the controller;
- Person in charge: Handles the communication between all parties (controller, operator, users and ANPD);
- ANPD: Brazil's regulatory institution ("Autoridade Nacional de Proteção de Dados"), that is responsible for fiscalization, rule defining and penalty application;
### Personal vs Sensitive Data

Basically, when we're talking about Privacy by Design, personal data is data that can be used to identify the user, such as the name, social security number, address, etc.

Sensitive data, on the other hand, could be used to cause harm or embarrassment for the user, such as ethnical origin, religious beliefs, political opinions, sexual life information, biometrical data, and so on.


- Proactive, not reactive while designing and developing software;
- Positive sum, not zero sum (avoid unnecessary trade-offs);

### Consent:

Consent is a term that needs to be clarified, so that we can obtain it from the user abiding the laws. Definition:

"Free, informed and unambiguous statement by which the holder agrees with the processing of their personal data for a certain purpose".

Can be given by written manifestation or other ways that prove the users want to consent. Can be revoked or excluded anytime.

### Punishment:

There are many punishments when breaking this law, such as a 2% penalty on all the company's revenue.

### Developing an app:

So, to develop an app, abiding to the LGPD, there should:

- Exist an analysis of the privacy impact (data inventory, data flowchart, risks);
- Be kept in mind the Privacy and Security by Design concepts and principles;
- Be defined an secure development cycle (security tests, DevSecOps, best practices);
- Exist an Privacy Policy that the users are informed about;
- Be consent, given by the user, to data and cookie collection.

## Security by Design:

Complements Privacy by Design, begin a software and hardware development metodology, aiming at building systems that are not vulnerable to attacks. Security by design identifies the problem on the lesser value step, and adds value and productivity to the system, as big problems are resolved earlier on the development process. Many of it is based on the information security pillars:

- Confidentiality: "is the property, that information is not made available or disclosed to unauthorized individuals, entities, or processes" [Wikipedia](https://en.wikipedia.org/wiki/Information_security);
- Integrity: "means maintaining and assuring the accuracy and completeness of data over its entire lifecycle, which means that data cannot be modified in an unauthorized or undetected manner" [Wikipedia](https://en.wikipedia.org/wiki/Information_security);
- Availability: "for any information system to serve its purpose, the information must be available when it is needed" [Wikipedia](https://en.wikipedia.org/wiki/Information_security);
- Authenticity: confirming that a sender/receiver is indeed the real and supposed to send/receive part;
- Non-repudiation: "implies one's intention to fulfill their obligations to a contract, and it also implies that one party of a transaction cannot deny having received a transaction, nor can the other party deny having sent a transaction" [Wikipedia](https://en.wikipedia.org/wiki/Information_security);

There's also the important Microsoft SSDL and OWASP principles:

### SSDL:

"The Microsoft Secure Software Development Lifecycle (SSDL) is a software development process designed and published by Microsoft back in January 2004. It was based on the spiral model of the SDLC. In the initial period of development, it was manly benefited the company to reduce the maintenance costs of the software, and improve the reliability", [Mr. Vic](https://faun.pub/microsofts-top-12-secure-software-development-lifecycle-ssdl-practices-for-software-developers-f54176667fb5).

- Stage 1: Education and Awareness (Training).
- Stage 2: Product requirement (security and privacy).
- Stage 3: Define and follow Design requirements (Best practices, protocols, - tools, documents).
- Stage 4: Define security features with cryptography standards.
- Stage 5: Metrics, Criteria, and compliance reporting.
- Stage 6: Product risk assessment (Define context, risk identification, risk - analysis, risk treatment).
- Stage 7: Manage and understand the Security Risk of Using Third-Party - Components.
- Stage 8: List of approved SDL tools.
- Stage 9: Static Analysis Security Testing (SAST).
- Stage 10: DynamicAnalysis Security Testing (DAST).
- Stage 11: Penetration Testing.
- Stage 12: Establish a Standard Incident Response Process (planning, Execution).

### OWASP:

"OWASP is an online community that produces free tools, documentation, articles, and technologies to help people secure their websites, web applications, and network resources. It provides a comprehensive list of security design principles that programmers should adhere to. Following these principles will ensure that your application is secure and dramatically reduces the risk of a successful cyber attack", [Patchstack](https://patchstack.com/security-design-principles-owasp/).

- Minimise attack surface area: "Every time a programmer adds a feature to their application, they are increasing the risk of a security vulnerability. The principle of minimizing attack surface area restricts the functions that users are allowed to access, to reduce potential vulnerabilities";
- Establish secure defaults: "This principle states that the application must be secure by default. That means a new user must take steps to obtain higher privileges and remove additional security measures (if allowed)";
- The principle of Least privilege: "The Principle of Least Privilege (POLP) states that a user should have the minimum set of privileges required to perform a specific task";
- The principle of Defence in depth: "The principle of defense in depth states that multiple security controls that approach risks in different ways are the best option for securing an application";
- Fail securely: "This principle states that applications should fail in a secure way. Failure should not give the user additional privileges, and it should not show the user sensitive information like database queries or logs";
- Don’t trust services: "Many web applications use third-party services for accessing additional functionality or obtaining additional data. This principle states that you should never trust these services from a security perspective";
- Separation of duties: "Separation of duties can be used to prevent individuals from acting fraudulently. For example, a user of an eCommerce website should not be promoted to also be an administrator as they will be able to alter orders and give themselves products. The reverse is also true — an administrator should not have the ability to do things that customers do, like order items from the front end of the website";
- Avoid security by obscurity: "This OWASP principle states that security by obscurity should never be relied upon. If your application requires its administration URL to be hidden so it can remain secure, then it is not secure at all";
- Keep security simple: "Developers should avoid the use of very sophisticated architecture when developing security controls for their applications. Having mechanisms that are very complex can increase the risk of errors";
- Fix security issues correctly: "If a security issue has been identified in an application, developers should determine the root cause of the problem. They should then repair it and test the repairs thoroughly".