FROM centos7-systemd
MAINTAINER "Olivier" <your@email.here>
# Created thanks to jperrin
# http://jperrin.github.io/centos/2014/09/25/centos-docker-and-systemd/
ENV container docker
RUN yum install -y openssh-server
RUN systemctl enable sshd
RUN ( groupadd -g 500 olivier ; useradd -g olivier -u 500 olivier )
RUN yum install -y wget
RUN ( cd /root ; wget https://dl.fedoraproject.org/pub/epel/7/x86_64/e/epel-release-7-2.noarch.rpm ; rpm -ivh epel-release-7-2.noarch.rpm )
RUN yum install -y nginx npm
RUN yum install -y xorg-x11-fonts-misc dejavu-fonts-common xorg-x11-fonts-100dpi xorg-x11-fonts-ISO8859-1-100dpi xorg-x11-fonts-75dpi xorg-x11-fonts-Type1
RUN echo -e "[google-chrome]\nname=google-chrome - \$basearch\nbaseurl=http://dl.google.com/linux/chrome/rpm/stable/\$basearch\nenabled=1\ngpgcheck=1\ngpgkey=https://dl-ssl.google.com/linux/linux_signing_key.pub\n" > /etc/yum.repos.d/google-chrome.repo
RUN yum install -y google-chrome-stable
#VOLUME [ "/sys/fs/cgroup" ]
#CMD ["/usr/sbin/init"]
