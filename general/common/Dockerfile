FROM fancl20/workspace:general-base

RUN apt-get update && apt-get install -y \
    clang cmake make pkg-config \
    golang \
    libostree-dev \
    jq && \
    mkdir -p /opt/zig && \
    curl -s https://ziglang.org/download/index.json \
    #| jq --raw-output 'del(.master) | to_entries | sort_by(.value.date) | .[-1].value."x86_64-linux".tarball' \
    | jq --raw-output '.master."x86_64-linux".tarball' \
    | xargs curl | tar --strip-components=1 -xJC /opt/zig && \
    ln -s /opt/zig/zig /usr/local/bin/ && \
    git clone --recurse-submodules https://github.com/zigtools/zls /opt/zls && \
    (cd /opt/zls && zig build) && \
    ln -s /opt/zls/zig-out/bin/zls /usr/local/bin/ && \
    rm -rf /tmp/* /var/lib/apt/lists/* /var/tmp/*

ENV CC=/usr/bin/clang CXX=/usr/bin/clang++