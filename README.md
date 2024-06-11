# How to create HTTPs Listerner with Application Load Balancer.
## Finish server set up which is running the application.
- Run Application with PM2.
- Set up NGINX Proxy and configuration file.
## Create Target Group:
- Target Type: Instances
- name
- Protocol: HTTP, Port: 80
- IP Type: IPv4
- Protocol Version: HTTP1
- Add instances to list on next page.
## Application Load Balancer:
- Name.
- Scheme: Internet-Facing.
- IP Address Type: IPv4
- Select VPC.
- AZ Selection.
- Security Group
- Listener and Router:
  - HTTP
  - 80
  - Target Group
- Create Load Balancer.
## HTTPS Listner Creation:
- 
