version: 0.1

# Policy Request Protocol

The Policy Request Protocol (PRP) defines communication between compliance systems and the Policy Server.  Its job is to define the query from the compliance system, and the response from the Policy Server.

## Definitions

* **Policy Server**: The TellTrail.org Policy Server stores data policies and communicates with compliance systems.
* **Compliance System**: Any system that implements the Data Compliance Specification.  Compliance Systems communicate with the Policy Server, and scrub noncompliant records from a Data Transfer Set, based on the response from the Policy Server.
* **Data Transfer Set**: A set of records containing data on Data Citizens, to be transferred to a third party.