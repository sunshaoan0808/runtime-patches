# qinglong 是基于 Alpine 的镜像，node 在 /usr/bin/node。
# 用官方 node:24.22.1-alpine 的 musl 二进制替换，修 2026-10 安全公告中的 Brotli/dns/TLS 漏洞。
FROM node:24.22.1-alpine AS nodebin
FROM whyour/qinglong:latest
COPY --from=nodebin /usr/local/bin/node /usr/bin/node
RUN node -v
