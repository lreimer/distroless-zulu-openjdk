ARG ZULU_VERSION
FROM azul/zulu-openjdk-centos:$ZULU_VERSION as builder

FROM gcr.io/distroless/base
LABEL maintainer="qaware-oss@qaware.de"

ENV LANG='en_US.UTF-8' LANGUAGE='en_US:en' LC_ALL='en_US.UTF-8'

ENV JAVA_HOME=/usr/lib/jvm/zulu11
ENV PATH=${PATH}:${JAVA_HOME}/bin

COPY --from=builder $JAVA_HOME $JAVA_HOME
COPY --from=builder /usr/lib64/libz.* /lib/x86_64-linux-gnu/

COPY --from=amd64/busybox:1.31.1 /bin/busybox /busybox/busybox
RUN ["/busybox/busybox", "--install", "/bin"]

CMD ["/bin/sh", "-c", "java -version"]
