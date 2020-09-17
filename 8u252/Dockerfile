ARG ZULU_VERSION
FROM azul/zulu-openjdk-centos:$ZULU_VERSION as builder

FROM gcr.io/distroless/base
LABEL maintainer="qaware-oss@qaware.de"

ENV JAVA_HOME=/usr/lib/jvm/zulu-8
ENV PATH=${PATH}:${JAVA_HOME}/bin

COPY --from=builder $JAVA_HOME $JAVA_HOME

COPY --from=amd64/busybox:1.31.1 /bin/busybox /busybox/busybox
RUN ["/busybox/busybox", "--install", "/bin"]

CMD ["/bin/sh", "-c", "java -version"]
