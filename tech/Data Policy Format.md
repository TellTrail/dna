version: 0.1

# Data Policy Format

A Data Policy is created by a Data Citizen and represents their wishes for the acceptable transfer of their data to third parties. A Data Policy can vary greatly in its complexity, depending on the wishes of its Data Citizen.

A Data Policy consists of the following format:

* **TTID**: The TellTrail ID for this Data Citizen.
* **Identifiers**: A list consisting of Identifiers for the Data Citizen.  Must contain at least one Identifier.
* **Default Letter Grade**: By default, the minimum letter grade required of a Data Consumer to receive this Data Citizen's record in a Data Transfer Set. Defaults to `C`.  Also may be *ALL* meaning all transfers are allowed, or *NONE* which means no transfers are allowed.
* **Type Cases**: Special cases for data types, as identified by entries from the Data Type Taxonomy.  More specific types (`shopping/music-instruments/guitars`) override more general types (`shopping`).  Type Cases override the Default Letter Grade, but are in turn overridden by the Whitelist and Blacklist. A dictionary consisting of entries, with each entry consisting of:
	* A key, which is the name of the data type (from the Data Type Taxonomy), and
	* A value, which is either the minimum letter grade required of the Data Consumer to receive the record, or *ALL* or *NONE*.
* **Whitelist**: A list of Data Consumer TTIDs, legal names or domains.  Transfers to these Data Consumers will always be allowed.
* **Blacklist**: A list of Data Consumer TTIDs, legal names or domains.  Transfers to these Data Consumers will never be allowed.  (A Data Consumer identifier cannot exist in both the whitelist and the blacklist).
