# 从上游公开源码构建 device-harvest，只把运行时 node 提到 24.22.1。
# 基础镜像仍用 playwright 1.63.0（Chromium 版本与 playwright 绑定）。
FROM mcr.microsoft.com/playwright:v1.63.0-noble

ARG NODE_VERSION=24.22.1
RUN curl -fsSL https://nodejs.org/dist/v${NODE_VERSION}/node-v${NODE_VERSION}-linux-x64.tar.gz \
      | tar -xz -C /usr/local --strip-components=1 \
 && node -v && npm -v

ENV PLAYWRIGHT_SKIP_BROWSER_DOWNLOAD=1 \
    NODE_ENV=production \
    PORT=8090

WORKDIR /app
COPY package.json package-lock.json ./
RUN npm ci --omit=dev && npm cache clean --force
COPY harvest.mjs docker-entrypoint.sh ./
RUN chmod +x docker-entrypoint.sh

EXPOSE 8090
ENTRYPOINT ["/app/docker-entrypoint.sh"]
CMD ["node", "harvest.mjs", "serve", "--port", "8090"]
