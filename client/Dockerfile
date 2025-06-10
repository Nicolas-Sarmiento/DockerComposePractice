FROM debian:bullseye-slim

RUN apt-get update && apt-get install -y \
    sshpass \
    ftp \
    net-tools \
    iputils-ping \
    && rm -rf /var/lib/apt/lists/*

RUN useradd -m -s /bin/bash douuser && \
    echo "douuser:dou123" | chpasswd

COPY setup.sh /usr/local/bin/setup.sh
RUN chmod +x /usr/local/bin/setup.sh && \
    echo "/usr/local/bin/setup.sh" >> /home/douuser/.bashrc

USER douuser
WORKDIR /home/douuser

CMD ["tail", "-f", "/dev/null"]