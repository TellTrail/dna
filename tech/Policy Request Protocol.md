version: 0.1

# Policy Request Protocol

The Policy Request Protocol (PRP) defines communication between compliance systems and the Policy Server.  Its job is to define the query from the compliance system, and the response from the Policy Server.

## Definitions

* **Policy Server**: The TellTrail.org Policy Server stores data policies and communicates with compliance systems.
* **Compliance System**: Any system that implements the Data Compliance Specification.  Compliance Systems communicate with the Policy Server, and scrub noncompliant records from a Data Transfer Set, based on the response from the Policy Server.
* **Data Transfer Set**: A set of records containing data on Data Citizens, to be transferred to a third party.
* **Data Type**: The nature of the data being transferred in the Data Transfer Set, for example: shopping, reading, browsing history, comments, health, etc.
* **Data Type Taxonomy**: A taxonomy of Data Types, for classification of data transferred within a Data Transfer Set.
* **Identifier**: A string that represents the identity of a Data Citizen.  A single Data Citizen may have multiple Identifiers. A Data Policy can be looked up with an Identifier.  Identifiers come in two formats:
	* A regular email address, designated as `name@domain`, e.g. `loren@example.com`.
	* A username for a service (such as a social network), designated as `username@@service-domain`, for example `telltrail@@twitter.com`.
* **Scrub Set**: A set of Identifiers, returned by the Policy Server, indicating which records should be scrubbed from the Data Transfer Set.
* **Policy Request**: A request from a Compliance System to the Policy Server, consisting of a set of Identifiers, and the TellTrail IDs of the Data Producer and the Data Consumer for the Data Transfer Set in question. The Policy Server will respond with a Scrub Set.

## Request Pre-Requirements

The Policy Request must be made under the following circumstances:

* The Data Producer (and if applicable, Data Exchange) must be registered with TellTrail and present their TTIDs.
* The Data Consumer *may* be registered with TellTrail. If so, they should be identified by TTID, otherwise by domain and/or legal name.
* The Policy Request must be conducted securely, over HTTPS.

## Request Format

The Policy Request is a JSON structure formatted as follows:

* Data Producer TTID
* Data Exchange TTID (Optional)
* Data Consumer TTID or Domain or Legal Name
	* Data Consumer Industry (Optional, used for non-registered Data Consumers)
* A list of Data Types representing the Data Transfer Set. Each Data Type will correspond to the Data Type Taxonomy.
* A list of Identifier tuples, with each tuple containing...
	* One or more Identifiers

Example:

	{"producer":"971b1001b38fd3888cd1",
	 "exchange":"0aa91f80d336a02a43ec",
	 "consumer":"www.example.com",
	 "types":["shopping/pharmacy","browsing"],
	 "identifiers":[["bonzo@clownsforcrime.org","BonzoSmythe"],["lulu@clownsforcrime.org"],["whatever@example.com"],["fred@example.com","FredFlintstone@@twitter.com"]]}

## Response Format

The Policy Server will respond to a Policy Request with a Scrub S	et, which will be formatted as follows:

* A response id, representing the Policy Server's specific response, made to a Policy Request at a specific time.
* A scrub set, consisting of a list of Identifier Tuples representing which records should be *removed* from the Data Transfer Set, with each tuple consisting of:
	* A list of one or more Identifiers

Example:

	{"response-id":"7c8d86f5a8bf9e369e4d",
	 "scrub":[["lulu@clownsforcrime.org"],["fred@example.com","FredFlintstone@@twitter.com"]}
	 

