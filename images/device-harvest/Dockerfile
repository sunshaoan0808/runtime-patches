# Playwright noble 镜像自带 node（当前 24.20.0），换成 24.22.1 官方 glibc 二进制。
FROM node:24.22.1-bookworm-slim AS nodebin
FROM mcr.microsoft.com/playwright:v1.63.0-noble
COPY --from=nodebin /usr/local/bin/node /usr/bin/node
RUN node -v
