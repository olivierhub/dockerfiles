FROM fedora20-systemd
MAINTAINER "Olivier" <your@email.here>
# Created thanks to jperrin
# http://jperrin.github.io/centos/2014/09/25/centos-docker-and-systemd/
ENV container docker
RUN yum install -y openssh-server
RUN systemctl enable sshd
RUN ( groupadd -g 500 olivier ; useradd -g olivier -u 500 olivier )
RUN yum install -y wget
RUN yum install -y git
RUN yum install -y xorg-x11-fonts-misc dejavu-fonts-common xorg-x11-fonts-100dpi xorg-x11-fonts-ISO8859-1-100dpi xorg-x11-fonts-75dpi xorg-x11-fonts-Type1
#RUN echo -e "[google-chrome]\nname=google-chrome - \$basearch\nbaseurl=http://dl.google.com/linux/chrome/rpm/stable/\$basearch\nenabled=1\ngpgcheck=1\ngpgkey=https://dl-ssl.google.com/linux/linux_signing_key.pub\n" > /etc/yum.repos.d/google-chrome.repo
#RUN yum install -y google-chrome-stable
# Xpra repository
RUN echo -e "[xpra]\nname=name=Xpra for Fedora \$releasever - \$basearch\ntype=rpm-md\nbaseurl=http://xpra.org/dists/Fedora/\$releasever/\$basearch\ngpgcheck=0\nenabled=1\n" > /etc/yum.repos.d/xpra.repo
# Wokaround for bug in the repo
#RUN ( cd /root ; wget http://xpra.org/dists/Fedora/20/x86_64/python-lz4-0.7.0-0.el7.centos.x86_64.rpm : wget http://xpra.org/dists/CentOS/7/x86_64/libfakeXinerama-0.1.0-3.el7.centos.x86_64.rpm ; yum -y install libfakeXinerama-0.1.0-3.el7.centos.x86_64.rpm python-lz4-0.7.0-0.el7.centos.x86_64.rpm xpra xterm screen )
RUN ( cd /root ; yum -y install xpra xterm screen )
# Start xpra as user olivier
RUN echo -e "[Unit]\nDescription=Xpra Startup\nAfter=sshd.service\n\n\n[Service]\nTimeoutStartSec=0\nType=simple\nExecStartPre=-/usr/bin/rm -f /run/nologin\nExecStart=/usr/bin/su olivier -c \"/usr/bin/xpra --no-notifications --no-pulseaudio --no-daemon --bind-tcp=0.0.0.0:5000 start :100 --start-child=xterm --exit-with-children\"\n#ExecStop=/usr/bin/su olivier -c \"/usr/bin/xpra stop :100\"\nRestart=always\n\n[Install]\nWantedBy=multi-user.target\n" > /usr/lib/systemd/system/xpra.service
RUN systemctl enable xpra 
#VOLUME [ "/sys/fs/cgroup" ]
#CMD ["/usr/sbin/init"]
