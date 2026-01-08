<h2>Step 1: Download the base and deployment package for the project.</h2>
Choose the corresponding base download based on server type, then download the full deployment package.<br><br>
Linux base <br>
x86 Chip  https://drive.google.com/file/d/1hswscioUr4pJgtZIvWwr5cuTR1vlQx5n/view?usp=sharing <br>
arm64 Chip  https://drive.google.com/file/d/1UlQjVExX149DWBFzuTteZQTMW_VGRVjx/view?usp=sharing
<br><br>
Mac base  <br>
https://drive.google.com/file/d/1QgaQly3bcy9Xp52H8K4r0-EtkOoyR72l/view?usp=sharing
<br><br>
Windows base  <br>
https://drive.google.com/file/d/1DhoMzZ_2NKgQlePckh0Uf3H2OlllLNYG/view?usp=sharing
<br><br>
<img width="225" height="229" alt="image" src="https://github.com/user-attachments/assets/b03ce5de-1553-4a62-9e02-d563fb68ba3d" />
<br><br>
<h2>Step 2: Select the server</h2>

<h4>Deployment Server - Configuration Recommendations</h4>
    <table>
        <thead>
            <tr>
                <th>Operating System</th>
                <th>Chip</th>
                <th>Server</th>
                <th>Number of Servers</th>
                <th>Server Configuration Suggestions</th>
                <th>Software Configuration (Installation Service Available)</th>
                <th>Supported Clouds</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>Linux/Windows<br>Recommended openEuler 22.03<br>Supports domestic Kylin OS</td>
                <td>x86<br>Supports ARM</td>
                <td>Supports Docker+K8S<br>Private Servers<br>Cloud Servers</td>
                <td>1 Server or 1 Docker Image</td>
                <td>CPU ≥ 2 Cores<br>Memory ≥ 4 GB</td>
                <td>MySQL 5.7 or above<br>Redis 4.0 or above</td>
                <td>Alibaba Cloud<br>Huawei Cloud<br>Tencent Cloud<br>AWS<br>Azure</td>
            </tr>
        </tbody>
    </table>

<h4>The following are non-essential middleware components; configure as needed.</h4>
    <table>
        <thead>
            <tr>
                <th>Type</th>
                <th>Supported</th>
                <th>Production Environment</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>File Storage</td>
                <td>Alibaba Cloud OSS<br>Tencent Cloud COS<br>Amazon S3<br>Microsoft Azure Blob Storage<br>Minio, Huawei Cloud OBS</td>
                <td>Recommended to add 1</td>
            </tr>
            <tr>
                <td>CDN</td>
                <td>Alibaba Cloud CDN<br>Tencent Cloud CDN, etc.</td>
                <td>Recommended to add 1</td>
            </tr>
        </tbody>
    </table>
<br><br>
<h2>Step 3: Practical Deployment</h2>
Before deployment, prepare a domain name (URL) for subsequent use.<br><br>

<h4>1、Installing MySQL and Redis</h4>

MySQL and Redis are two underlying databases that the IVX application relies on for operation. For large-scale commercial applications, we strongly recommend using cloud-hosted MySQL and Redis services, such as Alibaba Cloud's RDS and Cloud Database Redis Edition. We will detail the integration methods in later sections. Here, considering convenience and deployment costs, we will install MySQL and Redis locally on the server. Note: MariaDB can be used as an alternative to MySQL, as both are essentially equivalent.

Minimum software versions required:
MySQL: 5.7.9
Redis: 2.8

On CentOS, both software packages can be installed directly using the yum command. If issues arise, search online for detailed installation steps.

<h4>2、Create a directory and upload the program files</h4>


*SSH into the server<br>
We recommend using SSH to log into your Linux instance. Before logging in, you must know the server's administrator username and password.<br>
In the terminal, enter and execute the following command to connect to the Linux server:<br>
ssh username@hostname or IP address<br>
username is the default account obtained in the prerequisites.<br>
hostname or IP address is your Linux instance's public IP or custom domain name.<br>
If your local computer runs Mac OS, first open the built-in Terminal app before executing the command.<br>
If your local computer runs Linux, you can execute the command directly.<br>
If your local computer runs Windows 10 or Windows Server 2019, first open Command Prompt (CMD) before executing the command.<br>
Enter the obtained password and press Enter to complete the login.<br>
<img width="510" height="287" alt="image" src="https://github.com/user-attachments/assets/14bec44c-bfc1-4c38-b918-ce8ad18670c9" />

After successful login, you'll notice the terminal prefix changes from your desktop to the cloud server's name.<br>
You can enter the following command to view files in the current directory:<br>
ls<br>
<img width="200" height="49" alt="image" src="https://github.com/user-attachments/assets/8518ddd2-de22-4797-9cbf-2fdf7ec94eeb" />

Since this is a brand-new server, no files currently exist in this directory.<br>
Linux reports errors but not successes; therefore, if no error is displayed, the command executed correctly.<br>


*Create a new directory<br>
For easier management, create a directory named `testA` in the current server path by entering the following command in the terminal:<br>
mkdir testA<br>
<img width="285" height="79" alt="image" src="https://github.com/user-attachments/assets/2c09a1f7-1932-4e21-8cdd-f8869e3e19ad" />


*Upload the downloaded base and initial package<br>

