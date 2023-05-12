# notes


## Load Balancer Algorithms
- **Round Robin**: distributed across group of servers sequentially
- **Least Connections**: sent to server with fewest active connections
- **Least Time**: sent to server with fastest response time and fewest active connections
- **Hash**: distribution based on a key (e.g. IP address or Request URL)
- **IP Hash**
- **Random with Two Choices**: randomly pick 2 servers and select the one by least connections
