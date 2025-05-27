## Investigation: MiddleMayhem

# Scenario
The security team at MiddleMayhem Inc. has detected unusual network traffic to their admin portal, but no security breaches have been confirmed. Your SOC team has been provided 
with SIEM logs from the incident. Analyze the attack pattern to determine how attackers bypassed authentication, gained remote code execution, and moved laterally through the network.

# Questions
- Access the Website in the browser, present it in the bookmark, and identify the JavaScript framework and version used.
- Using Splunk, find the attacker’s IP address.
- Analyze the SIEM logs to determine how many unique URIs were accessed by the attacker.
- Explore the site and identify two specific locations that could reveal internal structures or potential access points not meant for public eyes. Provide the two relative URLs.
- Based on the Framework and Version, what recent CVE could be used to bypass authorization?
- Find the relevant HTTP header in the SIEM logs that indicates CVE exploitation. Provide the header name.
- What interesting URI did the attacker access after exploiting the CVE?
- The attacker tried uploading a reverse shell. Find out the IP and port to which the target would connect once the connection is established.
- After compromising the WebApp server, the attacker attempted lateral movement. Identify the technique used, as recorded in the SIEM logs.
- Identify the user account that achieved successful lateral movement to another server.

#Tools Used
- Splunk
- Next.JS
