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
- For healthchecks: might possible that it will always shows unhealthy status. To solve this issue increase **Timeout**, **Reduce Healthy threshold**
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
## Create SSL Certificate From ACM:
- Rquest Cetificate.
- Add Domains:
  - domain.com
  - *.domain.com
- View Certificate -> Copy `cname` records and edit it to your DNS Management from domain provider.
## HTTPS Listner Creation:
- Listener Configuration:
  - Protocol: HTTPS
  - Port: 443
- Target Group:
- Certificate: From ACM.
## Redirect HTTP to HTTPS.
- Edit HTTP listener
  - Change Routing action: Redirect to URL
  - Protocol: HTTPS
  - Port: 443
  - Status Code: 301 (permenetly moved)
## Domain Set up:
- Copy DNS of Application Load Balancer.
- Modify DNS Records.
- `CNAME` : `subdomain` : `alb.domain`
### Now you have completly set up HTTPS with Application Load Balancer.
