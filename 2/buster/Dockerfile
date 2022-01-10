
FROM xhofe/alist:latest AS origin

FROM debian:buster AS prod

# Container variables
ENV \
  TERM="xterm" \
  LANG="en_US.UTF-8" \
  LANGUAGE="en_US.UTF-8" \
  LC_ALL="en_US.UTF-8" \
  TIMEZONE="Asia/Shanghai"

RUN set -eux; \
        apt-get update; \
        apt-get install -y --no-install-recommends \
            curl \
            unzip \
            zsh \
            fuse \
        ; \
        curl https://rclone.org/install.sh | bash; \
        rm -rf /var/lib/apt/lists/*; \
        chsh -s $(which zsh); \
        sync

VOLUME /opt/alist/data/

WORKDIR /opt/alist/

COPY --from=origin /opt/alist/alist ./

EXPOSE 5244

CMD [ "./alist" ]
