FROM fancl20/workspace:general-base

RUN apt-get update && apt-get install -y \
    llvm cmake make pkg-config && \
    rm -rf /tmp/* /var/lib/apt/lists/* /var/tmp/*