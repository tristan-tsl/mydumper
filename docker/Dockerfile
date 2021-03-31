FROM debian:stable
WORKDIR /data
RUN set -ex \
    && echo "" > /etc/apt/sources.list \
    && echo "deb http://mirrors.aliyun.com/debian/ buster main non-free contrib" >> /etc/apt/sources.list \
    && echo "deb-src http://mirrors.aliyun.com/debian/ buster main non-free contrib" >> /etc/apt/sources.list \
    && echo "deb http://mirrors.aliyun.com/debian-security buster/updates main" >> /etc/apt/sources.list \
    && echo "deb http://mirrors.aliyun.com/debian/ buster-updates main non-free contrib" >> /etc/apt/sources.list \
    && echo "deb http://mirrors.aliyun.com/debian/ buster-updates main non-free contrib" >> /etc/apt/sources.list \
    && echo "deb-src http://mirrors.aliyun.com/debian/ buster-updates main non-free contrib" >> /etc/apt/sources.list \
    && echo "deb http://mirrors.aliyun.com/debian/ buster-backports main non-free contrib" >> /etc/apt/sources.list \
    && echo "deb-src http://mirrors.aliyun.com/debian/ buster-backports main non-free contrib" >> /etc/apt/sources.list \
    && apt-get update -y \
    && apt-get install -y wget \
    && wget https://github.com/maxbube/mydumper/releases/download/v0.10.1/mydumper_0.10.1-2.$(env -i bash -c '. /etc/os-release; echo $VERSION_CODENAME')_amd64.deb \
    && dpkg -i mydumper_0.10.1-2.$(env -i bash -c '. /etc/os-release; echo $VERSION_CODENAME')_amd64.deb \
    && rm -rf  mydumper_0.10.1-2.$(env -i bash -c '. /etc/os-release; echo $VERSION_CODENAME')_amd64.deb \
    && apt install -y libglib2.0-0 \
    && apt install -y libatomic1 \
    && ldd /usr/bin/mydumper \
    && mydumper -V