
```shell
root@asciinema:/home/gcs8# nano /etc/systemd/system/docker-compose-app.service
```

```shell
[Unit]
Description=Docker Compose Application Service
Requires=docker.service
After=docker.service

[Service]
Type=oneshot
RemainAfterExit=yes
WorkingDirectory=/root/asciinema
ExecStart=/usr/libexec/docker/cli-plugins/docker-compose up -d
ExecStop=/usr/libexec/docker/cli-plugins/docker-compose down
TimeoutStartSec=0

[Install]
WantedBy=multi-user.target
```

```shell
root@asciinema:~/asciinema# systemctl enable docker
Synchronizing state of docker.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable docker
```

```shell
root@asciinema:/home/gcs8# systemctl enable docker-compose-app
Created symlink /etc/systemd/system/multi-user.target.wants/docker-compose-app.service → /etc/systemd/system/docker-compose-app.service.
root@asciinema:/home/gcs8# reboot now
```

