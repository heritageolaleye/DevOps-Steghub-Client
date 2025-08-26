## BUILDING a MySQL Client-Server Setup

This project is all about the communication happening between clients and servers in a network. What We are going to do here is set up a MySQL Client-Server architecture using Amazon's cloud services and test to see things for ourselves.

## Step 1: Setting Up Our Virtual Machines

First, we need to create two virtual computers in the cloud. We will call one the **MySQL Serve** and the other the **MySQL Client**.

1. We will use Amazon's Ec2 service to create two virtual computers:

![project](/images/client.jpg)

![project2](/images/client2.jpg)

## Step 2: Setting Up Our MySQL Server

Now, let's set up the machine environment (our MySQL Server):

1. After creatiing the ec2 instance and doing all the preliminaries stated earlier, we will now connect to our server using a special key:

```bash
chmod 400 web.pem
ssh -i web.pem ubuntu@<ec2-ip-address>
```

2. Let's make sure our ec2 environment has all the latest packages:

```bash
sudo apt update && sudo apt upgrade -y
```
![project3](/images/client3.jpg)

3. Time to install MySQL Server – this is the service that we would like to access from the client machine which we would be setting up soon.

```bash
sudo apt install mysql-server -y
```
![project4](/images/client4.jpg)

4. Let's start and enable MySQL:

```bash
sudo systemctl status mysql
```

![project5](/images/client5.jpg)

3. Step 3: Setting Up Our MySQL Client

1. Let's connect to our client machine:

```bash
ssh -i web.pem ubuntu@<ec2-ip-address>
```

2. Update everything, just like we did for the server:

```bash
sudo apt update && sudo apt upgrade -y
```
3. Install MySQL Client – this action arms our client machine with the ability to connect, make requests and perform sql-like operations on our mysql-server instance/database:

```bash
sudo apt install mysql-client -y
```
![project6](/images/client6.jpg)

Step 4: Letting Our Client talk to our Server.

Now, we need to tell our server (MySQL Server) that it's okay for the client (MySQL Client) to peek inside and if necessary, perfom some operation. We can do this by changing some security settings:

![project7](/images/client7.jpg)

Step 5: Making Our Server More Welcoming

Let's set up our server to accept visitors:

1. Firstly, we will run a security script to make sure our server's configurations is safe and secure:

```bash
sudo mysql_secure_installation
```
![project8](/images/client8.jpg)


