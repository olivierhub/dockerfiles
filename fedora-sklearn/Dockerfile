FROM fedora
MAINTAINER "Olivier" <your@email.here>
ENV container docker
# Update distro
RUN dnf update -y
RUN dnf list all > /root/dnf_all
# Compilation tools
RUN dnf install -y gcc-gfortran gcc-c++ autoconf make
# Generic tools
RUN dnf install -y xterm screen bc
# Python2 packages
RUN dnf install -y python-pip python-scikit-learn opencv-python python-pandas python-psycopg2 python-pillow python-scikit-image python-statsmodels python-matplotlib python-pandas python-scikit-image python-setuptools python-crypto python-backports-ssl_match_hostname python-theano 
# Unpackaged python tools
RUN pip install nolearn
RUN pip install xgboost
RUN pip install holidays
# Editors, dev tools
RUN dnf install -y eclipse-pydev  dejavu-lgc-sans-mono-fonts dejavu-lgc-serif-fonts dejavu-lgc-sans-fonts dejavu-serif-fonts dejavu-sans-fonts dejavu-sans-mono-fonts dejavu-fonts-common liberation-fonts.noarch liberation-fonts-common.noarch liberation-narrow-fonts.noarch liberation-mono-fonts.noarch liberation-sans-fonts.noarch liberation-serif-fonts.noarch
#VOLUME [ "/sys/fs/cgroup" ]
#CMD ["/usr/sbin/init"]
