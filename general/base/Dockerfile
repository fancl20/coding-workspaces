FROM debian:testing

RUN apt-get update && apt-get install -y \
        dumb-init openssh-server curl git neovim fish && \
    mkdir /var/run/sshd /root/.ssh && \
    echo 'root:root' | chpasswd && \
    sed -ri 's/^#?PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config && \
    echo ${PUBLIC_KEY} >> /root/.ssh/authorized_keys && \
    rm -rf /tmp/* /var/lib/apt/lists/* /var/tmp/*

ENTRYPOINT ["dumb-init"]
CMD (cp /root/.ssh/authorized_keys_host /root/.ssh/authorized_keys && \
    chown root /root/.ssh/authorized_keys)> /dev/null; /usr/sbin/sshd -D