FROM node:8-alpine as builder
WORKDIR /app

RUN echo "https://mirrors.aliyun.com/alpine/v3.9/main/" > /etc/apk/repositories && \
    echo "https://mirrors.aliyun.com/alpine/v3.9/community/" >> /etc/apk/repositories && \
    echo "https://mirrors.aliyun.com/alpine/edge/testing/" >> /etc/apk/repositories && \
    apk add -U --no-cache --allow-untrusted tzdata chromium ttf-freefont wqy-zenhei ca-certificates && \
    mkdir -p /app /logs && \
    npm config set registry 'https://registry.npm.taobao.org' && \
    yarn config set registry 'https://registry.npm.taobao.org' && \
    yarn global add pm2 && \
    yarn cache clean && \
    rm -rf /var/cache/apk/*

COPY . .
RUN yarn clean && yarn install && yarn build
FROM nginx:alpine
COPY --from=builder /app/public /usr/share/nginx/html