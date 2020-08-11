FROM alpine:3.12
LABEL maintainer="<email_here>"
LABEL docker-id="docker_id"

RUN apk update && apk add --no-cache openssh
RUN mkdir /var/run/sshd
RUN adduser -h /home/foo -D foo
RUN echo 'foo:pass' | chpasswd
RUN sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin no/' /etc/ssh/sshd_config

# Generate ssh keys
RUN ssh-keygen -A
ENV NOTVISIBLE "in users profile"
RUN echo "export VISIBLE=now" >> /etc/profile

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]