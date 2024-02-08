Set up a local environment with AlmaLinux machine as the server with multiple websites, reverse proxy, forward proxy, and load balancing, follow these steps:

# Apache Server Setup for multiple website hosting:

1. Install Apache HTTP Server (httpd):
**sudo dnf install httpd**

2. Create Virtual Hosts for Multiple Websites:
Create configuration files for each virtual host under /etc/httpd/conf.d/ directory.
- /etc/httpd/conf.d/site1.conf
![image](https://github.com/dracarys20/localhosting/assets/56256359/696fd2e9-a746-4ae7-bbd4-f779b335e0d1)
- /etc/httpd/conf.d/site2.conf
![image](https://github.com/dracarys20/localhosting/assets/56256359/f768c982-bd46-4ac7-ab5e-07afb1a2862c)

3. Create directories for website files:
3.1 Make directory under /var/www/html/ directory.
- sudo mkdir /var/www/site1
- sudo mkdir /var/www/site2 

3.2 Set permissions
- sudo chown -R apache:apache /var/www/site1
- sudo chown -R apache:apache /var/www/site2

3.3 Create an _index.html_ for both site1 and site2
- echo "WELcum to SITE1 bugga" > /var/www/site1/index.html
- echo "WELcum to SITE2 bugga" > /var/www/site1/index.html

4. Add servers in hosts file
![image](https://github.com/dracarys20/localhosting/assets/56256359/e5738ef0-da06-48c5-ac98-6cfee241e129)

5.Enable and start Apache modules:
- sudo systemctl enable httpd
- sudo systemctl start httpd 

6. Verify it using curl
![image](https://github.com/dracarys20/localhosting/assets/56256359/bc9bd4c1-4872-45d3-8108-b91b68edf43d)

## Apache Server Setup for reverse proxy:

1. Configure Reverse Proxy:
Create a virtual host configuration file for proxy
![image](https://github.com/dracarys20/localhosting/assets/56256359/23924782-5029-4056-9de2-2bb81ff3d7e1)

2. Add rp.local to /etc/hosts 

3. Restart httpd and verify it using curl 
- sudo systemctl start httpd 
![image](https://github.com/dracarys20/localhosting/assets/56256359/c8b6e4e6-03cb-4207-8772-406666db735f)

## Apache Server Setup for load balancer:

1.
