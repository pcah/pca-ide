# https://gist.github.com/benjamintanweihao/29c85fcd598cc7ccab4c9b3baba3f96f
# docker run -it --rm --name sparkdev -e DISPLAY=${DISPLAY} -v `pwd`:/home/developer/SparkCourse -v /tmp/.X11-unix:/tmp/.X11-unix -v ~/.PyCharmCE2019.2:/home/developer/.PyCharmCE2019.2 -p 4040:4040 benjamintanweihao/sparkdev
# docker exec -it sparkdev /opt/pycharm/bin/pycharm.sh
FROM jrei/systemd-ubuntu:18.04

RUN apt-get update \
 && apt-get install -y locales \
 && dpkg-reconfigure -f noninteractive locales \
 && locale-gen C.UTF-8 \
 && /usr/sbin/update-locale LANG=C.UTF-8 \
 && echo "en_US.UTF-8 UTF-8" >> /etc/locale.gen \
 && locale-gen \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

# Users with other locales should set this in their derivative image
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

RUN apt-get update \
 && apt-get install -y \
    curl \
    unzip \
    python3 \
    python3-setuptools \
 && ln -s /usr/bin/python3 /usr/bin/python \
 && easy_install3 pip py4j \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*
ENV PYTHONIOENCODING UTF-8
ENV PIP_DISABLE_PIP_VERSION_CHECK 1

###### JAVA & PYTHON #######

RUN apt-get update \
 && apt-get install --no-install-recommends -y \
  curl \
  gcc \
  git \
  less \
  libfontconfig1 \
  libfreetype6-dev \
  libgtk2.0-0 \
  libxext-dev \
  libxrender-dev \
  libxslt1.1 \
  libxtst-dev \
  libxxf86vm1 \
  openjdk-8-jre \
  openssh-client \
  python \
  python-dev \
  python-pip \
  python-setuptools \
  python3 \
  python3-dev \
  python3-pip \
  python3-setuptools \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/* \
 && useradd -ms /bin/bash developer

###### SNAP #######

RUN apt-get update \
 && apt-get install --no-install-recommends -y \
  snapd fuse \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/* \
 && useradd -ms /bin/bash developer

###### PYCHARM #######

WORKDIR /opt/pycharm
USER developer

RUN systemctl start snapd \
  && snap install pycharm-professional --classic \

CMD ["/snap/bin/pycharm-professional"]
