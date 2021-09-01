# AWS
## **Wednesday 1/9**:
### INSERT IMAGE
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

1. Install NGINX and launch on public IP to ensure access to AWS resources

alot of stuff

Run `cd app` then `npm start` after booting up machine
    - Check IP and :3000
    - Can't see port :3000 --> need to select instant, click Security Group, edit inbound rule, add rule tcp 3000 allow from anywhere IPv6 0.0.0.0
