FROM fancl20/workspace:general-base

RUN apt-get update && apt-get install -y \
    clang cmake make pkg-config \
    golang \
    libostree-dev && \
    rm -rf /tmp/* /var/lib/apt/lists/* /var/tmp/*

ENV CC=/usr/bin/clang CXX=/usr/bin/clang++