FROM alpine:3.7

LABEL maintainer="mritd <mritd1234@gmail.com>"

ARG TZ="Asia/Shanghai"

ENV TZ ${TZ}
ENV IDGEN_VERSION v0.0.2
ENV IDGEN_DOWNLOAD_URL https://github.com/mritd/idgen/releases/download/${IDGEN_VERSION}/idgen_linux_amd64

RUN apk upgrade --update \
    && apk add bash tzdata wget ca-certificates \
    && wget ${IDGEN_DOWNLOAD_URL} -O /usr/local/bin/idgen \
    && chmod +x /usr/local/bin/idgen \
    && ln -sf /usr/share/zoneinfo/${TZ} /etc/localtime \
    && echo ${TZ} > /etc/timezone \
    && apk del wget ca-certificates \
    && rm -rf /var/cache/apk/*

EXPOSE 8080

CMD ["idgen","server"]
