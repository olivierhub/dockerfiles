FROM centos7-systemd-angular
MAINTAINER "Olivier" <your@email.here>
# Created thanks to jperrin
# http://jperrin.github.io/centos/2014/09/25/centos-docker-and-systemd/
ENV container docker
# Xpra repository
RUN echo -e "[xpra]\nname=name=Xpra for Centos \$releasever - \$basearch\ntype=rpm-md\nbaseurl=http://xpra.org/dists/CentOS/\$releasever/\$basearch\ngpgcheck=0\nenabled=1\n" > /etc/yum.repos.d/xpra.repo
# Wokaround for bug in the repo
RUN ( cd /root ; wget http://xpra.org/dists/CentOS/7/x86_64/python-lz4-0.7.0-0.el7.centos.x86_64.rpm : wget http://xpra.org/dists/CentOS/7/x86_64/libfakeXinerama-0.1.0-3.el7.centos.x86_64.rpm ; yum -y install libfakeXinerama-0.1.0-3.el7.centos.x86_64.rpm python-lz4-0.7.0-0.el7.centos.x86_64.rpm xpra xterm screen )
# Start xpra as user olivier
RUN echo -e "[Unit]\nDescription=Xpra Startup\nAfter=sshd.service\n\n\n[Service]\nTimeoutStartSec=0\nType=simple\nExecStartPre=-/usr/bin/rm -f /run/nologin\nExecStart=/usr/bin/su olivier -c \"/usr/bin/xpra --no-notifications --no-pulseaudio --no-daemon --bind-tcp=0.0.0.0:5000 start :100 --start-child=xterm --exit-with-children\"\n#ExecStop=/usr/bin/su olivier -c \"/usr/bin/xpra stop :100\"\nRestart=always\n\n[Install]\nWantedBy=multi-user.target\n" > /usr/lib/systemd/system/xpra.service
RUN systemctl enable xpra 
#VOLUME [ "/sys/fs/cgroup" ]
#CMD ["/usr/sbin/init"]
