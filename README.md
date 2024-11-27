# tcpdump1_network_traffic_lab.pcap
Capturing and analysing packets by tcpdump

This tcpdump session successfully captured packets, demonstrating network activity over HTTP (port 80). Here's a breakdown of what happened:

    Interface Status:
        The ifconfig output confirms that wlan0 (the wireless interface) is active with IP 192.168.1.48.

    Capturing Packets:
        Running tcpdump -i wlan0 -nn -c9 port 80 -w capture.pcap filtered for traffic on port 80 and saved it to capture.pcap.

    Inspecting Captured Packets:
        Using tcpdump -nn -r capture.pcap -v revealed:
            An HTTP GET request from the machine (192.168.1.48) to opensource.google.com (resolved to 142.251.16.101).
            The server responded with an HTTP 301 redirect, instructing the client to access https://opensource.google/.

    Hex and ASCII View:
        The command tcpdump -nn -r capture.pcap -X showed the packet data in both hex and ASCII formats. It highlighted:
            HTTP headers (GET / HTTP/1.1, Host: opensource.google.com) in the payload.
            The redirection response in the server’s reply.

Observations:

    Curl was used to make the HTTP request, as shown in the User-Agent field.
    The server enforced HTTPS by redirecting HTTP traffic.

For extracting specific details (e.g., HTTP headers or payloads), it can be used by Wireshark to open the capture.pcap file for a GUI-based analysis. 
