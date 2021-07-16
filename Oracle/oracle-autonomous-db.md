# Setting up your own database with Oracle Autonomous Database
What you can do to take control of the data you use for projects

---

As a student who with an active interest in creating personal projects in the pursuit of learning, one of the biggest roadblocks when kickstarting any project is the data. 

I wanted a solution that:
* allows for the reusability of data, without having to reset the data environment each time
* able to be accessed from multiple platforms and languages
* provide confidence that the data being used is updated and allows full control over what data I have access to
* allows for potential apis that can be created without the need for dedicated server

### Project Structure

#### Why Cloud?

#### Why Oracle?
One benefit for using Oracle instead of other cloud providers for personal projects is because of Oracle's Always Free products. Unlike AWS or Azure where your cloud resources require payment after 12 months of free use, you can keep your Oracle instances free permanently. 

Oracle Always Free Tier Highlights:
* 2 Oracle Autonomous Databases with 20GB capacity
* 2 Oracle Compute Virtual machines
* 10GB Object Storage
* 2 Block Volumes Storage with 200GB capacity

### Setting up an Oracle Cloud account

### Creating an autonomous database

### Connecting to autonomous database

#### Access requirements
You can provide external access to your database through a client credentials wallet. This wallet can be downloaded from your database's menu page on the Oracle Console. 

1. Download the wallet to the device you want database access to
2. Set a password for the wallet you downloaded
3. Unzip the wallet to a local folder. Default folder path is '/home/user/Oracle/network/admin' or 'C:/Users/user/Oracle/netowrk/admin
4. Using a text editor, open the ojdbc.properties file and follow the given steps:
    * uncomment the bottom lines that start with 'javax'
    * comment out the oracle.net.wallet_location property
    * set the password where specified (trustStorePassword and keyStorePassword)

#### Connecting through Oracle Database Actions

1. Login to your Oracle cloud console
2. Search for Autonomous Database
3. Select the database you want to access
4. Click on Tools and then go to Database Actions
5. Enter your login information

#### Connecting through Visual Studio Code

1. Download Visual Studio Code 
2. Go to the Extensions and type in 'Oracle'
3. Install the Oracle Developer Tools for VS Code
4. Install the most recent version of .Net Core
5. Click the database icon on the sidebar to open up the Oracle Developer Tools
6. Click the plus sign next to database
7. Enter your connection information in the new Oracle Connection tab that opened up
    * Connection Type: TNS Alias
    * TNS Admin Location: <file path to unzipped wallet\>
    * TNS Alias: <any of the dropdown options\>
    * Wallet File Location: <file path to unzipped wallet\>
    * Role: Default
    * User name: Username
    * Password: Password
8. Click create connection

#### Connecting through SQLcl (SQL command line)

#### Connecting to Tableau
1. Open up Tableau Desktop
2. On the connect menu, select Oracle 
3. Enter your connection information in the following window
    * Server: <tns_name of server to connect to\>
    * Enter information to sign into server: username & password
    * Require SSL: check the box only
4. Click Sign In

---
\* tns_name will be one of values listed in the tnsnames.ora file within your wallet. Sample tns_name: dbname_high