
Some useful Wireshark http filters.

- `http.request.method == “METHOD”`  
    Hunting for repeated or unusual requests can be useful
- `http.request.uri contains “.php”`  
    Can be helpful in finding suspicious or modified files
- `http.user_agent`   
    Used to locate unusual or outdated User-Agents