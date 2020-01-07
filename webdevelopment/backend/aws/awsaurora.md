# AWS Aurora:
## Introduction:
Amazon Aurora (Aurora) is a fully managed relational database engine that's compatible with MySQL and PostgreSQL. By this definition, you can imply that you don't need to learn different querys, just SQL, and use it. At least at first glance.
## Concepts:
- Cluster: one or more DB instances and a cluster volume that manages the data for them. A cluster volume is a virtual database storage volume that spans multiple Availability Zones, with each Availability Zone having a copy of the DB cluster data.

--Primary DB Instance: Performs the operations;

--Aurora Replica: Only read operations, and can be located on different Availability Zones.

