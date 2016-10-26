FROM node:6.9.1

RUN apt-get update -qq && apt-get install -y build-essential chrpath libssl-dev libxft-dev
RUN apt-get install -y ruby && gem install sass && gem install bourbon

RUN mkdir /app
WORKDIR /app

CMD ["bash", "start.sh"]
