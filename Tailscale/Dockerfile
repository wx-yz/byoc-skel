FROM tailscale/tailscale:latest

RUN mkdir /tmp/tailscale-state && \
    chown 10014:10014 /tmp/tailscale-state

ENV TS_STATE_DIR=/tmp/tailscale-state
ENV TS_USERSPACE=true

USER 10014
