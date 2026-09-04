# Lab

Core Assignment – Domain + EC2 + DNS

## Topics involved

This Assignment combines the principal concepts of networking; IPs, firewalls, routing, DNS, ports and cloud hosting

## Objective

Required steps include the following:
1.	Buy and configure a domain.
2.	Deploy an EC2 instance.
3.	Security group must allow HTTP (port 80).
4.	Install and run NGINX.
5.	Create an A Record and map it to your EC2 public IPv4 Address.
6.	View your domain page and ensure the NGINX landing page is displayed.

## Steps
1. [domain purchas](01-domain-purchase.png) - Using Route 53, I purchased the domain robelk.co.uk
2. [EC2 running instance](02-EC2-running-instance.png) - Selected t2 micro Amazon linux to Deploy as the EC2 running instance
3. [Security group allows port80](03-Security-group-allows-port80.png) - Navigating to the Security Group inbound section, selecting inbound traffic on port80 from 0.0.0.0 /0 (all IPv4 addresses) enables HTTP access to the instance.
4. [Nginx installation](04-Nginx-installation.png) - Commands used:
   - `sudo yum install -y nginx` – sudo privileges are required to install NGINX on the EC2 instance.
   - `sudo systemctl enable nginx` – tells the system to start NGINX when the server reboots, preventing it from having to be manually started.
   - `sudo systemctl start nginx` – starts NGINX on the system. NGINX listens on port 80 for web requests.
5. [A record](05-A-record.png) - Using Route 53 from my knowledge on DNS, I navigated to hosted zones to create an A Record mapping it to the EC2 Running instance by using its public IP Address. This enables the domain page to display the NGINX Landing Page.
6. [domain page showing nginx landing page](06-domain-page-showing-nginx-landing-page.png) - Verified the NGINX Landing Page was displayed on the domain page.
