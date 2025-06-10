FROM fedora:latest

RUN dnf install -y vsftpd && dnf clean all

COPY vsftpd.conf /etc/vsftpd/vsftpd.conf

RUN useradd -m samuel && echo "samuel:abc123" | chpasswd
RUN useradd -m jose && echo "jose:abc123" | chpasswd
RUN useradd -m nicolas && echo "nicolas:abc123" | chpasswd

RUN mkdir -p /home/samuel/ftp/files && chown -R samuel:samuel /home/samuel/ftp && chmod -R 755 /home/samuel/ftp
RUN mkdir -p /home/jose/ftp/files && chown -R jose:jose /home/jose/ftp && chmod -R 755 /home/jose/ftp
RUN mkdir -p /home/nicolas/ftp/files && chown -R nicolas:nicolas /home/nicolas/ftp && chmod -R 755 /home/nicolas/ftp
RUN mkdir -p /var/run/vsftpd/empty

EXPOSE 20 21 10000-10010

CMD ["/usr/sbin/vsftpd", "/etc/vsftpd/vsftpd.conf"]