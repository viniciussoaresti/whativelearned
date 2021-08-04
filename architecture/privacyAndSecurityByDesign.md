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