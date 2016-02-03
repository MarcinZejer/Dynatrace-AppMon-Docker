FROM alpine:3.3

MAINTAINER Martin Etmajer <martin.etmajer@dynatrace.com>

ENV VERSION             "6.2"
ENV INSTALLER_FILE_NAME "dynatrace-agent-unix.jar"
ENV INSTALLER_URL       "http://downloads.dynatracesaas.com/${VERSION}/${INSTALLER_FILE_NAME}"

ENV DT                  "/opt/dynatrace"
ENV LIB64               "${DT}/agent/lib64/libdtagent.so"

ENV INSTALL_DEPS        "curl openjdk8-jre-base"

RUN apk add --no-cache ${INSTALL_DEPS} && \
    curl -L -o /tmp/${INSTALLER_FILE_NAME} ${INSTALLER_URL} && \
    java -jar /tmp/${INSTALLER_FILE_NAME} -b 64 -t ${DT} -y && \
    apk del ${INSTALL_DEPS} && \
    rm -rf /tmp/*

CMD while true; do sleep 1; done