FROM node:latest

MAINTAINER li liangquan

ENV HOST 0.0.0.0
EXPOSE 3000

RUN mkdir -p /app
COPY . /app
WORKDIR /app
RUN npm config set registry https://registry.npm.taobao.org
RUN npm install
RUN npm run build

CMD [ "npm", "start" ]
