# CVE-2024-27198

### CVE-2024-27198 - Authentication Bypass Using an Alternate Path vulnerability in JetBrains TeamCity Server

- Please refer to Rapid7's blogpost for more information: [CVE-2024-27198 and CVE-2024-27199: JetBrains TeamCity Multiple Authentication Bypass Vulnerabilities](https://www.rapid7.com/blog/post/2024/03/04/etr-cve-2024-27198-and-cve-2024-27199-jetbrains-teamcity-multiple-authentication-bypass-vulnerabilities-fixed/)

![teamcityserverlogo](https://www.devopsschool.com/blog/wp-content/uploads/2022/04/teamcity-logo.png)

*Products and Versions affected:*


| Product  | Affected Versions |
| :--------| :---------------- |
| TeamCity Server | <= 2023.11.3|

- **CVSS:** 9.8
- **Actively Exploited:** [YES](https://www.cisa.gov/news-events/alerts/2024/03/07/cisa-adds-one-known-exploited-jetbrains-vulnerability-cve-2024-27198-catalog)
- **Patch:** YES
- **Mitigation:** YES

# Lab

You can deploy a TeamCity server with Docker to test this exploit

- Download a vulnerable TeamCity Server docker image, for this case version: 2023.11.3
```
docker pull jetbrains/teamcity-server:2023.11.3
```

- Then run the docker container

```
docker run -it -d --name teamcity -u root -p 8111:8111 jetbrains/teamcity-server:2023.11.3
```

- Finally, go to: `http://localhost:8111` and follow the configuration instructions for your new server (just click `Proceed` and create a new admin account).

# Help

```
usage: CVE-2024-27198.py [-h] -t TARGET -u USERNAME -p PASSWORD

options:
  -h, --help            show this help message and exit
  -t TARGET, --target TARGET
                        Target TeamCity Server URL
  -u USERNAME, --username USERNAME
                        Insert username for the new user
  -p PASSWORD, --password PASSWORD
                        Insert password for the new user
```

**Example:** 

```
python CVE-2024-27198.py -t http://localhost:8111 -u mynewadminuser -p mypassword
```


# References

- [CVE-2024-27198 and CVE-2024-27199: JetBrains TeamCity Multiple Authentication Bypass Vulnerabilities (FIXED)](https://www.rapid7.com/blog/post/2024/03/04/etr-cve-2024-27198-and-cve-2024-27199-jetbrains-teamcity-multiple-authentication-bypass-vulnerabilities-fixed/)
- [Additional Critical Security Issues Affecting TeamCity On-Premises (CVE-2024-27198 and CVE-2024-27199) – Update to 2023.11.4 Now](https://blog.jetbrains.com/teamcity/2024/03/additional-critical-security-issues-affecting-teamcity-on-premises-cve-2024-27198-and-cve-2024-27199-update-to-2023-11-4-now/)
- [CISA Adds One Known Exploited JetBrains Vulnerability, CVE-2024-27198, to Catalog](https://www.cisa.gov/news-events/alerts/2024/03/07/cisa-adds-one-known-exploited-jetbrains-vulnerability-cve-2024-27198-catalog)
- [GreyNoise Tag - TeamCity JetBrain CVE-2024-27198 Auth Bypass Attempt](https://viz.greynoise.io/query/tags:%22TeamCity%20JetBrain%20CVE-2024-27198%20Auth%20Bypass%20Attempt%22)
