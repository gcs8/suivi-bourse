
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

