# Cybersecurity Incident Report:

# Network Traffic Analysis

## Part 1: Provide a summary of the problem found in the DNS and ICMP traffic log.

Based on the results of the network analysis from tcp dump log, to retrieve the IP address of the website www.yummyrecipesforme.com, the UDP protocol was used as part of the DNS protocol. The ICMP protocol responded with an error message which shows that there are issues with DNS server.

The first two lines in each tcp dump log shows the UDP message from the browser to the DNS server. The third and the fourth line shows that the ICMP echo reply returned the error message: udp port 53 unreachable.

It is evident that the issue lies with the DNS server as port 53 is associated with protocol traffic and is used for listening of receiving requests of IP address lookup by the DNS server. There are further issues with DNS performance as there is the plus sign after the query identification number 35084 signifying that the query is not a simple one and may have additional parameters or features enabled.
The A? indicates that the DNS query is asking for an A (Address) record. An A record maps a domain name to an IPv4 address. The ? signifies that this is a query (a request for information) rather than a response.

The ICMP error message suggest that the DNS server received a UDP query for domain name retrieval with additional flags, but the server was unable to process it due to the udp port 53 unreachable error and therefore not responding.

<!--The most likely issue is: the UDP message requesting an IP address for the domain "www.yummyrecipesforme.com" did not go through to the DNS server because no service was listening on the receiving DNS port. This may indicate a problem with the web server or the firewall configuration. It is a possible indication of a DDOS attack that has overwhelmed the server with requests making the port busy and unable to listen to other requests.-->

## Part 2: Explain your analysis of the data and provide at least one cause of the incident.

The incident occurred today (date) at 13:24pm

## Explain how the IT team became aware of the incident:

The incident occurred in the afternoon when several customers of clients reported that they were not able to access the client company website www.yummyrecipesforme.com, and saw the error “destination port unreachable” after waiting for the page to load.

## Explain the actions taken by the IT department to investigate the incident:

The cybersecurity team providing IT services are currently investigating the issue so customers can access the website again.

## Note key findings of the IT department's investigation (i.e., details related to the port affected, DNS server, etc.):

The security team responded and began running tests by first visiting the website and saw the same error “destination port unreachable” and then ran tests with the network protocol analyzer tool (packet sniffing tool) tcpdump by loading the webpage again.

The resulting tcpdump logs revealed that port 53, which is used for listening or receiving requests of IP address lookup by the DNS server: 203.0.113.2.domain, is unreachable as the ICMP echo error replied as UDP port 53 unreachable.

The next step is to investigate whether the DNS server is down or traffic to port 53 is blocked by the firewall or is configured correctly.

## Note a likely cause of the incident:

Most like causes of the incident could be that the DNS server is down due to overloading requests by a successful Denial of Service (DoS) attack or a firewall or network security rule is blocking UDP traffic on port 53, which is used for DNS queries, or the DNS server's configuration may be incorrect, such as missing or invalid IP bindings for port 53.
