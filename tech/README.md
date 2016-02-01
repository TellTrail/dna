version: 0.1

# Technology in TellTrail

One column of TellTrail is technology.  There is a collection of technology projects which support the TellTrail initiative.

## Policy Server

Paramount is the Policy Server.   This project's goal is to create a scaleable online service that acts as an arbiter of whether a data transfer is permissable according to a Data Citizen's policy.  There is only one policy server, operated by TellTrail.org, and it contains all data policies.

There will be a **Policy Request Protocol (PRP)** that defines communication with the Policy Server.

## Reference Data Compliance Library

This is a reference implementation of a data compliance library.  It it responsible for sending queries to the TellTrail Policy Server regarding data transfers, and then scrubbing noncompliant records from the data transfer sets, based on the response from the Policy Server.

There will be a **Data Compliance Specification** that defines the reference Data Compliance Library.