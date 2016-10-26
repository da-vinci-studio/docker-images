FROM node:6.9.1

RUN apt-get update -qq && apt-get install -y build-essential chrpath libssl-dev libxft-dev
RUN apt-get install -y ruby && gem install sass && gem install bourbon

RUN mkdir -p /app /home/docker && \
    groupadd -r docker && \
    useradd -u 1000 -r -g docker -d /home/docker -s /sbin/nologin docker && \
    chown -R docker:docker /home/docker && \
    chown -R docker:docker /app

WORKDIR /app

CMD ["bash", "start.sh"]
