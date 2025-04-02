# Cybersecurity Incident Report

## Section 1: Identify the type of attack that may have caused this network interruption

One potential explanation for the website's connection timeout error message is a DoS attack.

The logs show that the web server is flooded with SYN packet requests which caused it to stop responding.

This event could be a network level denial of service (DoS) attack, called a **SYN flood attack**, that targets network bandwidth to slow traffic. A SYN flood attack simulates a TCP connection and floods the server with SYN packets

## Section 2: Explain how the attack is causing the website to malfunction

When website visitors try to establish a connection with the web server, a three-way handshake occurs using the TCP protocol. Explain the three steps of the handshake:

1. Initially, the source sends a SYN packet to the destination server, requesting to connect

2. Secondly, the destination server sends back a SYN-ACK packet agreeing to connect.

3. Finally, the source sends an ACK packet acknowledging the destination's permission response.

To create denial-of-service, an attacker exploits the fact that after an initial SYN packet has been received, the server will respond back with one or more SYN/ACK packets and wait for the final step in the handshake.

The attacker sends a high volume of SYN packets to the targeted server. The server then responds to each connection request and leaves an open port ready to receive the response. While the server waits for the final ACK packet, which never arrives, the attacker continues to send more SYN packets. The arrival of each new SYN packet causes the server to temporarily maintain a new open port connection for a certain length of time. Once all available ports have been utilized, the server is unable to function normally.

The web server has experienced a significant issue stemming from a large number of SYN packet requests originating from a single IP address. This influx has overwhelmed the server’s capacity to process incoming requests, resulting in connection timeouts for new visitors.
