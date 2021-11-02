FROM debian:stable
WORKDIR /data
RUN set -ex \
    && echo "" > /etc/apt/sources.list \
    && echo "deb http://mirrors.aliyun.com/debian/ buster main non-free contrib" >> /etc/apt/sources.list \
    && echo "deb-src http://mirrors.aliyun.com/debian/ buster main non-free contrib" >> /etc/apt/sources.list \
    && echo "deb http://mirrors.aliyun.com/debian-security buster/updates main" >> /etc/apt/sources.list \
    && echo "deb http://mirrors.aliyun.com/debian/ buster-updates main non-free contrib" >> /etc/apt/sources.list \
    && echo "deb-src http://mirrors.aliyun.com/debian/ buster-updates main non-free contrib" >> /etc/apt/sources.list \
    && echo "deb http://mirrors.aliyun.com/debian/ buster-backports main non-free contrib" >> /etc/apt/sources.list \
    && echo "deb-src http://mirrors.aliyun.com/debian/ buster-backports main non-free contrib" >> /etc/apt/sources.list \
    && apt-get update -y \
    && apt-get install -y wget \
    && apt install -y libglib2.0-0 \
    && apt install -y libatomic1 \
    && wget https://github.com/maxbube/mydumper/releases/download/v0.11.3/mydumper_0.11.3-1-zstd-80.$(env -i bash -c '. /etc/os-release; echo $VERSION_CODENAME')_amd64.deb \
#    && wget ftp://10.28.40.62/mydumper/mydumper_0.11.3-1-zstd-80.$(env -i bash -c '. /etc/os-release; echo $VERSION_CODENAME')_amd64.deb \
    && dpkg -i mydumper_0.11.3-1-zstd-80.$(env -i bash -c '. /etc/os-release; echo $VERSION_CODENAME')_amd64.deb \
    && rm -rf  mydumper_0.11.3-1-zstd-80.$(env -i bash -c '. /etc/os-release; echo $VERSION_CODENAME')_amd64.deb \
    && ldd /usr/bin/mydumper \
    && mydumper -V