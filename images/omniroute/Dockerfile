# 保留 resin-sticky 定制层，仅替换运行时 node。
FROM node:24.22.1-bookworm-slim AS nodebin
FROM ghcr.io/sunshaoan0808/omniroute-base:3.8.48-resin-sticky
COPY --from=nodebin /usr/local/bin/node /usr/local/bin/node
RUN node -v
