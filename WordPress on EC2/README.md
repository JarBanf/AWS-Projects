# WordPress on EC2
Amazon Elastic Compute Cloud (Amazon EC2) provides on-demand, scalable computing capacity in the Amazon Web Services (AWS) Cloud. You can use Amazon EC2 to launch as many or as few virtual servers as you need, configure security and networking, and manage storage. On a virtual server you can install an Apache web server to host your WordPress website.

**Tasks**
- [Step 1: Create a key pair](#step-1-create-a-key-pair)
- [Step 2: Create a security group](#step-2-create-a-security-group)
- [Step 3: Create & connect to instance](#step-3-create--connect-to-instance)
- [Step 4: Install packages](#step-4-install-packages)
- [Step 5: Create a database user and database for WordPress](#step-5-create-a-database-user-and-database-for-wordPress)
- [Step 6: Enable & Test TLS](#step-6-enable--test-tls)

### Step 1: Create a key pair
### Step 2: Create a security group
### Step 3: Create & connect to instance
### Step 4: Install packages

1. Perform quick update to make sure all software packages are up to date.

```
sudo dnf update -y
```

2. Install the latest versions of Apache web server and PHP packages.

```
sudo dnf install wget php-mysqlnd httpd php-fpm php-mysqli mariadb105-server php-json php php-devel -y
```

3. Download the latest WordPress installation package

```
sudo wget https://wordpress.org/latest.tar.gz
```

4. Unzip and unarchive the installation package. The installation folder is unzipped to a folder called `wordpress`.

```
sudo tar -xzf latest.tar.gz
```

### Step 5: Create a database user and database for WordPress

WordPress installation needs to store information, such as blog posts and user comments, in a database. This procedure helps you create your blog's database and a user that is authorized to read and save information to it.

1. Secure the database server
The default installation of the MariaDB server has several features that are great for testing and development, but they should be disabled or removed for production servers. The mysql_secure_installation command walks you through the process of setting a root password and removing the insecure features from your installation.

1a. Start the MariaDB server.

```
sudo systemctl start mariadb httpd
```
