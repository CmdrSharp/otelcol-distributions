FROM alpine:3.19 as certs
RUN apk --update add ca-certificates

FROM scratch

ARG USER_UID=10001
USER ${USER_UID}

COPY --from=certs /etc/ssl/certs/ca-certificates.crt /etc/ssl/certs/ca-certificates.crt
COPY --chmod=755 otelcol-ext /otelcol-ext
COPY config.yaml /etc/otelcol-ext/config.yaml
ENTRYPOINT ["/otelcol-ext"]
CMD ["--config", "/etc/otelcol-ext/config.yaml"]
EXPOSE 4317 55678 55679
