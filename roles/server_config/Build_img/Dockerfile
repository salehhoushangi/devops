FROM alpine:latest

# latest certs
#RUN apk add ca-certificates --no-cache && update-ca-certificates

# timezone support
ENV TZ=Asia/Tehran
RUN apk add --update tzdata --no-cache &&\
    cp /usr/share/zoneinfo/${TZ} /etc/localtime &&\
    echo $TZ > /etc/timezone
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime 
# install chrony and place default conf which can be overridden with volume
RUN apk add --no-cache chrony && mkdir -p /etc/chrony
COPY chrony_server.conf /etc/chrony/chrony.conf

# port exposed
EXPOSE 123/udp

# start
CMD [ "/usr/sbin/chronyd", "-d", "-s"]
