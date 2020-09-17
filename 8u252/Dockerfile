ARG ZULU_VERSION
FROM azul/zulu-openjdk-centos:$ZULU_VERSION as build

FROM gcr.io/distroless/base
LABEL maintainer="qaware-oss@qaware.de"

ENV JAVA_HOME=/usr/lib/jvm/zulu-8
ENV PATH=${PATH}:${JAVA_HOME}/bin

COPY --from=build $JAVA_HOME $JAVA_HOME

COPY --from=amd64/busybox:1.31.1 /bin/busybox /busybox/busybox
RUN ["/busybox/busybox", "--install", "/bin"]

ENTRYPOINT ["/bin/sh"]
