# Independent Website System Features

## PC Version
- **Pages**
  - Homepage
  - Search
  - Details Page
  - Order Page
  - Checkout
- **Features**
  - Email Subscription
  - Inquiry System
  - Customer Service System
  - Shopping & Checkout
  - Payment Gateways
    - PayPal
    - USDT
    - T/T
  - News System
  - Coupons
    - Store Coupons
      - Verify if already claimed upon redemption
    - Product Coupons
  - SEO Enhancement: GEO Structure

## Mobile Version
- **Pages**
  - Homepage
  - Search
  - Details Page
  - Shopping Page
  - Order Page
  - Checkout
  - My Account
- **Features**
  - Email Subscription
  - Inquiry System
  - Customer Service System
  - Shopping & Checkout
  - Payment Gateways
    - PayPal
    - USDT
    - T/T
  - News System
  - Coupons
  - Order Management
  - Account Settings
  - SEO Enhancement: GEO Structure

## Backend (Admin)
- **User PC**
  - Shopping Cart
  - Inquiry Management
  - Subscription Management
  - Order Management
  - Review Management
  - Coupons
  - Account Settings
- **Product Management**
  - Publish Products
  - Manage Products
- **Add-to-Cart Management**
- **Inquiry Management**
- **Transaction Management**
  - Subscription Management
  - Review Management
  - Order Management
- **Company Information**
- **Merchant Backend**
  - Store Management
    - Homepage Banners
    - Staff Management
    - ERP System
  - News Management
    - Article Management
    - Category Management
  - Marketing Management
    - Coupons
  - Customer Management
  - Settings
    - Account Settings

## Step 1: Download the base and deployment package for the project

Choose the corresponding base download based on server type, then download the full deployment package.

**Linux base**  
x86 Chip: https://drive.google.com/file/d/1hswscioUr4pJgtZIvWwr5cuTR1vlQx5n/view?usp=sharing  
arm64 Chip: https://drive.google.com/file/d/1UlQjVExX149DWBFzuTteZQTMW_VGRVjx/view?usp=sharing

**Mac base**  
https://drive.google.com/file/d/1QgaQly3bcy9Xp52H8K4r0-EtkOoyR72l/view?usp=sharing

**Windows base**  
https://drive.google.com/file/d/1DhoMzZ_2NKgQlePckh0Uf3H2OlllLNYG/view?usp=sharing

![image](https://github.com/user-attachments/assets/b03ce5de-1553-4a62-9e02-d563fb68ba3d)

## Step 2: Select the server

### Deployment Server - Configuration Recommendations

| Operating System | Chip | Server | Number of Servers | Server Configuration Suggestions | Software Configuration (Installation Service Available) | Supported Clouds |
|-----------------|------|--------|-------------------|----------------------------------|-------------------------------------------------------|------------------|
| Linux/Windows<br>Recommended openEuler 22.03<br>Supports domestic Kylin OS | x86<br>Supports ARM | Supports Docker+K8S<br>Private Servers<br>Cloud Servers | 1 Server or 1 Docker Image | CPU ≥ 2 Cores<br>Memory ≥ 4 GB | MySQL 5.7 or above<br>Redis 4.0 or above | Alibaba Cloud<br>Huawei Cloud<br>Tencent Cloud<br>AWS<br>Azure |

### The following are non-essential middleware components; configure as needed

| Type | Supported | Production Environment |
|------|-----------|------------------------|
| File Storage | Alibaba Cloud OSS<br>Tencent Cloud COS<br>Amazon S3<br>Microsoft Azure Blob Storage<br>Minio, Huawei Cloud OBS | Recommended to add 1 |
| CDN | Alibaba Cloud CDN<br>Tencent Cloud CDN, etc. | Recommended to add 1 |

## Step 3: Practical Deployment

Before deployment, prepare a domain name (URL) for subsequent use.

### 1. Installing MySQL and Redis

MySQL and Redis are two underlying databases that the IVX application relies on for operation. For large-scale commercial applications, we strongly recommend using cloud-hosted MySQL and Redis services, such as Alibaba Cloud's RDS and Cloud Database Redis Edition. We will detail the integration methods in later sections. Here, considering convenience and deployment costs, we will install MySQL and Redis locally on the server. Note: MariaDB can be used as an alternative to MySQL, as both are essentially equivalent.

Minimum software versions required:
- MySQL: 5.7.9
- Redis: 2.8

On CentOS, both software packages can be installed directly using the yum command. If issues arise, search online for detailed installation steps.

### 2. Create a directory and upload the program files

**SSH into the server**  
We recommend using SSH to log into your Linux instance. Before logging in, you must know the server's administrator username and password.

In the terminal, enter and execute the following command to connect to the Linux server:
```
ssh username@hostname or IP address
```

- `username` is the default account obtained in the prerequisites.
- `hostname or IP address` is your Linux instance's public IP or custom domain name.

If your local computer runs Mac OS, first open the built-in Terminal app before executing the command.
If your local computer runs Linux, you can execute the command directly.
If your local computer runs Windows 10 or Windows Server 2019, first open Command Prompt (CMD) before executing the command.

Enter the obtained password and press Enter to complete the login.

![image](https://github.com/user-attachments/assets/14bec44c-bfc1-4c38-b918-ce8ad18670c9)

After successful login, you'll notice the terminal prefix changes from your desktop to the cloud server's name.

You can enter the following command to view files in the current directory:
```
ls
```

![image](https://github.com/user-attachments/assets/8518ddd2-de22-4797-9cbf-2fdf7ec94eeb)

Since this is a brand-new server, no files currently exist in this directory.
Linux reports errors but not successes; therefore, if no error is displayed, the command executed correctly.

**Create a new directory**  
For easier management, create a directory named `testA` in the current server path by entering the following command in the terminal:
```
mkdir testA
```

![image](https://github.com/user-attachments/assets/2c09a1f7-1932-4e21-8cdd-f8869b3e19ad)

**Upload the downloaded base and initial package**

![image](https://github.com/user-attachments/assets/ad538cfc-5ac5-4349-92c5-fcd37b6ca2a1)

**Use scp to upload two files to the newly created folder**  
To upload files to the server, open a new terminal window and enter the following command to upload files to the server:
```
scp filepath username@IP address:path/
```

Replace `<filepath>` with the path to the file you want to upload. Ensure the path contains no Chinese characters. You can drag and drop the file directly into the terminal to resolve the path. To upload multiple files simultaneously, separate them with spaces.

`username@IP address:path/` specifies your Linux instance's public IP and the destination directory.

Below is the input from the example. After pressing Enter, the files are uploaded to the specified directory.

![image](https://github.com/user-attachments/assets/b4f75ce6-75f7-407b-b1b8-a28bb5bfe0cf)

**Server window: Navigate to the newly created folder**  
Switch back to the previous terminal and enter the following command to change to the testA directory:
```
cd testA/
```

Then enter `ls` to view files in this path. You will find both the base deployment package and application deployment package have been successfully uploaded.

![image](https://github.com/user-attachments/assets/0b9a05db-d41e-450c-9741-cb37abc5c0ca)

**Set ivxbase as an executable file**  
Next, in this path, enter the following command to make ivxbase an executable file:
```
chmod +x ivxbase
```

When you use `ls` again, you will see ivxbase highlighted in green, indicating success.

![image](https://github.com/user-attachments/assets/3b97dc72-7c20-4b32-8f81-fbb351988fae)

### 3. Initialize ivxbase

**Run ivxbase**  
Next, enter the following command in the current directory to run ivxbase:
```
./ivxbase
```

![image](https://github.com/user-attachments/assets/a3d074cf-e5e9-45f8-920f-23b5623968b0)

**Begin filling in configuration items**  
Note that these settings will be saved in the config file, so don't panic if you make a mistake—you can modify the configuration file later.

**Enter the port number**  
Note: Since you will configure Nginx or a load balancer later, avoid using port 80. Choose a different custom port, such as 9966.

![image](https://github.com/user-attachments/assets/3ff8573d-2fdc-4195-8dbe-bedd84ceffc8)

**Enter the Redis address and user**  
For single-machine deployment, use the locally installed Redis. Use all default options and press Enter.

![image](https://github.com/user-attachments/assets/f08d1c2d-f703-4de6-990b-10935f04a4ec)

**Enter the MySQL address, user, and password**  
For single-machine deployment, use the locally installed MySQL/MariaDB. Correctly enter the username and password. For the database, you can use the default `h5work` or specify your own. Enter any memorable English name.

![image](https://github.com/user-attachments/assets/3d182b30-02a4-498a-9592-15a35708b64a)

*Note: This demo uses Alibaba Cloud RDS database. If using locally installed MySQL, leave the address field as default.*

**After running the command**  
The application path will be printed in the command line, indicating successful deployment. You can now access the demo via IP address + port. Note: When customizing the path, the application will retain this custom path during export.

![image](https://github.com/user-attachments/assets/612b664b-a9c0-4275-bdbc-ad9fcd1dd779)

Access the demo using `IP:port/path` (where `path` is the directory specified after `path:` upon successful import).
```
http://39.104.21.197:9966/play/n11fB3WO
```

Press `Ctrl+C` in the terminal to stop the demo process.
