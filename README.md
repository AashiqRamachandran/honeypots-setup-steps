# How To Set Up A Honeypot On AWS EC2 

Set up Ubuntu as an EC2 machine. 
* 4 VCPU, 16GB RAM Configuration
Allow all traffic in the security group config
Connect to the EC2 machine via the console session manager
Prep
* apt-get update
* apt install python3-pip
* fuser 21/tcp


Install Honeypots 
* pip3 install honeypots
* Create config file using vi config.json


```{
  "logs": "file,terminal,json",
  "logs_location": "/var/log/honeypots/",
  "syslog_address": "",
  "syslog_facility": 0,
  "postgres": "",
  "sqlite_file":"",
  "db_options": [],
  "sniffer_filter": "",
  "sniffer_interface": "",
  "honeypots": {
    "ftp": {
      "port": 21,
      "ip": "0.0.0.0",
      "username": "ftp",
      "password": "anonymous",
      "log_file_name": "ftp.log",
      "max_bytes": 10000,
      "backup_count": 10,
      "options":["capture_commands"]
    }
  }
}
```

* screen
* sudo -E python3 -m honeypots --setup ftp --config config.json
* Detach screen




Simulate attackers using replit
* Log into https://replit.com/@ramachandranaas/honeypots
* Install FTP
* Open an FTP console (ftp)
* open
* Username: ftp, password: anonymous
* Run some commands (ls, cd)




Check logs 
* cd /var/log/honeypots
* tail ftp.log
