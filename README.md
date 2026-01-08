<h2>Step 1: Download the base and deployment package for the project.</h2>
<br><br>
Linux base <br>
x86  https://file3.ih5.cn/ivxbase/v2.1.22/ivxbase <br>
arm64  https://file3.ih5.cn/ivxbase/v2.1.22/ivxbase_arm64
<br><br>
Mac base  <br>
https://file3.ih5.cn/ivxbase/v2.1.22/ivxbase_mac
<br><br>
Windows base  <br>
https://file3.ih5.cn/ivxbase/v2.1.22/ivxbase.exe
<br><br>
<img width="225" height="229" alt="image" src="https://github.com/user-attachments/assets/b03ce5de-1553-4a62-9e02-d563fb68ba3d" />
<br><br>
<h2>Step 2: Select the server</h2>

<br><br>
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
