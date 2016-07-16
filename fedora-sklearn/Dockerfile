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
RUN dnf install -y python-pip python-scikit-learn opencv-python python-pandas python-psycopg2 python-pillow python-scikit-image python-statsmodels python-matplotlib python-pandas python-scikit-image python-setuptools python-crypto python-backports-ssl_match_hostname python-theano h5py pyephem PyXB pygame
# Unpackaged python tools
RUN ( pip install nolearn ; pip install lasagne ; pip install xgboost ; pip install holidays; pip install git+https://github.com/dnouri/nolearn.git@master#egg=nolearn==0.7.git ; pip install seaborn ; pip install keras ; pip install statistics )
# Editors, dev tools
RUN dnf install -y eclipse-pydev  dejavu-lgc-sans-mono-fonts dejavu-lgc-serif-fonts dejavu-lgc-sans-fonts dejavu-serif-fonts dejavu-sans-fonts dejavu-sans-mono-fonts dejavu-fonts-common liberation-fonts.noarch liberation-fonts-common.noarch liberation-narrow-fonts.noarch liberation-mono-fonts.noarch liberation-sans-fonts.noarch liberation-serif-fonts.noarch
# rpm fusion
RUN dnf install -y http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-23.noarch.rpm http://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-23.noarch.rpm
# CUDA ENV
RUN yum install -y kmod-nvidia-4.2.3-300.fc23.x86_64.x86_64
#RUN ( wget http://developer.download.nvidia.com/compute/cuda/repos/fedora21/x86_64/cuda-repo-fedora21-7.5-18.x86_64.rpm ; rpm -ivh cuda-repo-fedora21-7.5-18.x86_64.rpm ; yum install -y cuda ; dnf  install -y compat-gcc-34-c++-3.4.6-37.fc23.x86_64 compat-gcc-34-3.4.6-37.fc23.x86_64 ; ln -sf /usr/bin/g++34 /usr/local/cuda/bin/g++ ; ln -sf /usr/bin/gcc34 /usr/local/cuda/bin/gcc )
RUN ( yum install -y http://developer.download.nvidia.com/compute/cuda/repos/fedora21/x86_64/cuda-repo-fedora21-7.5-18.x86_64.rpm ; yum install -y cuda-7.5 ; sed -i 's,^#error -- unsupported GNU version! gcc versions later than 4.9 are not supported!,#warning -- unsupported GNU version! gcc versions later than 4.9 are not supported!,' /usr/local/cuda-7.5/bin//../targets/x86_64-linux/include/host_config.h )
# system tools
RUN ( dnf install -y strace tmux gnome-terminal )
#VOLUME [ "/sys/fs/cgroup" ]
#CMD ["/usr/sbin/init"]
#DEVICE [ --device /dev/nvidia0:/dev/nvidia0 --device /dev/nvidiactl:/dev/nvidiactl --device /dev/nvidia-uvm:/dev/nvidia-uvm ]
