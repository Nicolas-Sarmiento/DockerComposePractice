FROM debian:bullseye-slim

RUN apt-get update && apt-get install -y \
    openssh-server \
    && rm -rf /var/lib/apt/lists/*

RUN mkdir /var/run/sshd

# Copy welcome script and make it executable
COPY welcome.sh /usr/local/bin/welcome.sh
RUN chmod +x /usr/local/bin/welcome.sh

# Create user and configure welcome message
RUN useradd -m -s /bin/bash jkl && echo "jkl:123s" | chpasswd && echo "/usr/local/bin/welcome.sh" >> /home/jkl/.bashrc
RUN useradd -m -s /bin/bash jose && echo "jose:123s" | chpasswd && echo "/usr/local/bin/welcome.sh" >> /home/jose/.bashrc
RUN useradd -m -s /bin/bash samuel && echo "jkl:123s" | chpasswd && echo "/usr/local/bin/welcome.sh" >> /home/samuel/.bashrc
RUN useradd -m -s /bin/bash nicolas && echo "jkl:123s" | chpasswd && echo "/usr/local/bin/welcome.sh" >> /home/nicolas/.bashrc

# Configure SSH
RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin no/' /etc/ssh/sshd_config && \
    sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/' /etc/ssh/sshd_config

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]
