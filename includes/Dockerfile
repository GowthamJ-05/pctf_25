FROM ubuntu:22.04 AS custom

RUN apt-get update && \
        apt-get install -y libc6 && \
        rm -rf /var/lib/apt/lists/

RUN export LD_LIBRARY_PATH=/usr/lib/x86_64-linux-gnu/


FROM pwn.red/jail

COPY --from=custom / /srv

ENV JAIL_PIDS=30
ENV JAIL_TIME=60
ENV JAIL_PORT=7001

COPY bin/*.pdf /srv/app/
COPY bin/Vault_of_Lost_Memories /srv/app/run

EXPOSE 7001/tcp