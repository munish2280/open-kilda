# Copyright 2017 Telstra Open Source
#
#   Licensed under the Apache License, Version 2.0 (the "License");
#   you may not use this file except in compliance with the License.
#   You may obtain a copy of the License at
#
#       http://www.apache.org/licenses/LICENSE-2.0
#
#   Unless required by applicable law or agreed to in writing, software
#   distributed under the License is distributed on an "AS IS" BASIS,
#   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
#   See the License for the specific language governing permissions and
#   limitations under the License.
#

FROM kilda/base-ubuntu

ENV DEBIAN_FRONTEND noninteractive
ENV MININET_REPO https://github.com/mininet/mininet.git
ENV MININET_INSTALLER mininet/util/install.sh
ENV INSTALLER_SWITCHES -fbinptvwyx

RUN apt-get update && apt-get -qy install mininet net-tools tcpdump \
    inetutils-ping autoconf automake ca-certificates git libtool \
    openssh-client patch vim python-bottle python-jsonschema python-scapy \
    && rm -rf /var/lib/apt/lists/*
RUN pip install python-logstash
RUN ln -s /usr/sbin/tcpdump /usr/bin/tcpdump

ADD app /app
RUN chmod 777 /app/*

WORKDIR /tmp

VOLUME ["/data"]

WORKDIR /data

# Default command.
CMD ["bash"]
