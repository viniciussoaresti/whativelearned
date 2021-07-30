# Privacy and Security by Design:

Course offered by Instituto Atlântico, discussing about privacy, LGPD, security and programming techniques.

## Privacy by Design:

First of all, since around 2016, a lot of discussions about personal data privacy are taking place in the world, producing, as a result, privacy laws, such as GDPR (EU), CCPA (California) and LGPD (Brazil).

There's been a lot of system attacks, including ransomware cases, and they're even worse in this pandemic context we're living (2020-2021). So there's even more focus to this topic than it already had, specially when we're talking about designing new components and systems. So we should, by design (not only on our implementation), protect the user's privacy.

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

### Personal vs Sensitive Data

Basically, when we're talking about Privacy by Design, personal data is data that can be used to identify the user, such as the name, social security number, address, etc.

Sensitive data, on the other hand, could be used to cause harm or embarrassment for the user, such as ethnical origin, religious beliefs, political opinions, sexual life information, biometrical data, and so on.


- Proactive, not reactive while designing and developing software;
- Positive sum, not zero sum (avoid unnecessary trade-offs);