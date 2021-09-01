# AWS
## **Wednesday 1/9**:
##### **INSERT IMAGE**
 Previously, we have been working using *monolith architecture*. 

#### **Today's tasks**:
- Create machine `Linux ubuntu 16.04 - EC2`
- Need to copy app code with `provision.sh`
- Install required dependancies (nodejs, nginx, reverse proxy etc.)
- Security groups for Linux/EC2 instance
- Allow public IP with required ports
from local host to cloud, `ssh`
    - need AWS credentials
    - AWS key
    - sre.pem file save into ssh folder in local host
- MUST NOT SHARE AWS KEYS ANYWHERE --> DO NOT PUSH IT GITHUB OR ANY PUBLIC CLOUD

### Creating new AWS machine

1. Install NGINX and launch on public IP to ensure access to AWS resources

2. Create instanace on AWS
    - Launch instances
        - `Amazon Machine Type`: Ubuntu Server 16.04 LTS (HVM), SSD Volume Type -- 64-bit
        - `Instance Type`: t2.micro
        - `Configure Instance Details`: 
        *Number of instances:* 1
        *Network:* default
        *Subnet:* DevOpsStudent default 1a
        *Auto-assign Public IP:* Enable
        - `Storage`: Keep settings
        - `Add Tags`: `Name` `SRE_akunma_app`
        - `Security`:
        *Group Name:* SRE_akunma_app
        *Description:* SRE_akunma_app
        *Type:* SSH *Source:* My IP *Description:* From my IP
        `Add Rule`
        *Type:* HTTP *Source:* Anywhere *Decription:* ???

3. In GitBash, `cd` into home and create new directory `.ssh`

4. Download SRE_key and place inside `.ssh`
    - Back to Launch instance wizard --> Click `Launch` --> *Choose an existing key pair*, sre_key|RSA

5. Click on the instance then `connect`
    - Follow instructions under `SSH client` tab
    - Run instance in GitBash using last text string

**Make sure to run all the dependancies that are outlined in the previous cloud_computing_intro repo**

6. Copy app folder from previous `Vagrantfile` into new machine.
From the `Vagrantfile` directory:
```bash
scp -ri ~/.ssh/sre_key.pem app ubuntu@*Public IP address
*:/home/ubuntu/app
```
7. Run `cd app` then `npm start` after booting up machine
    - Check IP and :3000
    - Can't see port :3000

8. Back on instances page, select the instance 
    - From the Security tab, click on the security group, edit inbound rules and add a new rule
    *Type:* Custom TCP *Port Range:* 3000 *Source:* Anywhere IPv4 0.0.0.0/0
    - Save rules

9. Run machine again, `npm start` --> paste IP address in search bar and the app is running


