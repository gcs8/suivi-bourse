
```shell
root@suivibourse:/usr/local/suivibourse/# nano /etc/systemd/system/docker-compose-app.service
```

```shell
[Unit]
Description=Docker Compose Application Service
Requires=docker.service
After=docker.service

[Service]
Type=oneshot
RemainAfterExit=yes
WorkingDirectory=/usr/local/suivibourse/suivi-bourse-3.7.2/docker-compose
ExecStart=/usr/libexec/docker/cli-plugins/docker-compose up -d
ExecStop=/usr/libexec/docker/cli-plugins/docker-compose down
TimeoutStartSec=0

[Install]
WantedBy=multi-user.target
```

```shell
root@suivibourse:/usr/local/suivibourse/# systemctl enable docker
Synchronizing state of docker.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable docker
```

```shell
root@suivibourse:/usr/local/suivibourse/# systemctl enable docker-compose-app
Created symlink /etc/systemd/system/multi-user.target.wants/docker-compose-app.service → /etc/systemd/system/docker-compose-app.service.
root@suivibourse:/usr/local/suivibourse/# reboot now
```

```bash
root@suivibourse:/home/gcs8# systemctl status docker-compose-app
● docker-compose-app.service - Docker Compose Application Service
     Loaded: loaded (/etc/systemd/system/docker-compose-app.service; enabled; vendor preset: enabled)
     Active: active (exited) since Sat 2024-07-06 02:17:45 UTC; 26s ago
    Process: 1470 ExecStart=/usr/libexec/docker/cli-plugins/docker-compose up -d (code=exited, status=0/SUCCESS)
   Main PID: 1470 (code=exited, status=0/SUCCESS)
        CPU: 128ms

Jul 06 02:17:45 suivibourse systemd[1]: Starting Docker Compose Application Service...
Jul 06 02:17:45 suivibourse docker-compose[1470]:  Container suivi-bourse-prom  Running
Jul 06 02:17:45 suivibourse docker-compose[1470]:  Container suivi-bourse-app  Running
Jul 06 02:17:45 suivibourse docker-compose[1470]:  Container suivi-bourse-graf  Running
Jul 06 02:17:45 suivibourse systemd[1]: Finished Docker Compose Application Service.
```
