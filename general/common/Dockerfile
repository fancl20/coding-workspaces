FROM fancl20/workspace:general-base

RUN echo 'deb https://dl.bintray.com/dryzig/zig-debian bullseye main' >> /etc/apt/sources.list && \
    apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 379CE192D401AB61 && \
    apt-get update && apt-get install -y \
    clang cmake make pkg-config \
    golang \
    zig \
    libostree-dev && \
    rm -rf /tmp/* /var/lib/apt/lists/* /var/tmp/*

ENV CC=/usr/bin/clang CXX=/usr/bin/clang++