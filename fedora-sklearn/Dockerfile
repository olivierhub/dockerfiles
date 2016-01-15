FROM fedora
MAINTAINER "Olivier" <your@email.here>
ENV container docker
# Update distro
RUN dnf update -y
RUN dnf list all > /root/dnf_all
# Compilation tools
RUN dnf install -y gcc-gfortran gcc-c++ autoconf make
# Generic tools
RUN dnf install -y xterm screen bc git vim wget procps-ng
# Python2 packages
RUN dnf install -y python-pip python-scikit-learn opencv-python python-pandas python-psycopg2 python-pillow python-scikit-image python-statsmodels python-matplotlib python-pandas python-scikit-image python-setuptools python-crypto python-backports-ssl_match_hostname python-theano 
# Unpackaged python tools
RUN ( pip install nolearn ; pip install lasagne ; pip install xgboost ; pip install holidays; pip install git+https://github.com/dnouri/nolearn.git@master#egg=nolearn==0.7.git )
# Editors, dev tools
RUN dnf install -y eclipse-pydev  dejavu-lgc-sans-mono-fonts dejavu-lgc-serif-fonts dejavu-lgc-sans-fonts dejavu-serif-fonts dejavu-sans-fonts dejavu-sans-mono-fonts dejavu-fonts-common liberation-fonts.noarch liberation-fonts-common.noarch liberation-narrow-fonts.noarch liberation-mono-fonts.noarch liberation-sans-fonts.noarch liberation-serif-fonts.noarch
# CUDA ENV
RUN ( wget http://developer.download.nvidia.com/compute/cuda/repos/fedora21/x86_64/cuda-repo-fedora21-7.5-18.x86_64.rpm ; rpm -ivh cuda-repo-fedora21-7.5-18.x86_64.rpm ; yum install -y cuda ; dnf  install -y compat-gcc-34-c++-3.4.6-37.fc23.x86_64 compat-gcc-34-3.4.6-37.fc23.x86_64 ; ln -sf /usr/bin/g++34 /usr/local/cuda/bin/g++ ; ln -sf /usr/bin/gcc34 /usr/local/cuda/bin/gcc )
#VOLUME [ "/sys/fs/cgroup" ]
#CMD ["/usr/sbin/init"]
#DEVICE [ --device /dev/nvidia0:/dev/nvidia0 --device /dev/nvidiactl:/dev/nvidiactl --device /dev/nvidia-uvm:/dev/nvidia-uvm ]
