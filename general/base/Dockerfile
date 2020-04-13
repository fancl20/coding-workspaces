FROM debian:testing

RUN apt-get update && apt-get install -y \
        curl git neovim jq fish && \
    CODE_RELEASE=$(curl -sX GET "https://api.github.com/repos/cdr/code-server/releases/latest" \
        | awk '/tag_name/{print $4;exit}' FS='[""]'); \
    CODE_URL=$(curl -sX GET "https://api.github.com/repos/cdr/code-server/releases/tags/${CODE_RELEASE}" \
        | jq -r '.assets[] | select(.browser_download_url | contains("linux-x86_64")) | .browser_download_url') && \
    mkdir -p /app/code-server && curl -L "${CODE_URL}" | tar xz -C /app/code-server --strip-components=1 && \
    rm -rf /tmp/* /var/lib/apt/lists/* /var/tmp/*

ENTRYPOINT [ "/app/code-server/code-server" ]