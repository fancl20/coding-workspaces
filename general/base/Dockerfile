FROM debian:testing

RUN apt-get update && apt-get upgrade -y && apt-get install -y \
        dumb-init openssh-server curl git neovim fish rsync build-essential && \
    mkdir /var/run/sshd /root/.ssh && \
    echo 'root:root' | chpasswd && \
    sed -ri 's/^#?PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config && \
    sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config && \
    echo ${PUBLIC_KEY} >> /root/.ssh/authorized_keys && \
    rm -rf /tmp/* /var/lib/apt/lists/* /var/tmp/*

ENTRYPOINT ["dumb-init"]
CMD (rsync -a /root/.ssh_host/ /root/.ssh && chown -R root:root /root/.ssh)> /dev/null; \
    /usr/sbin/sshd -D