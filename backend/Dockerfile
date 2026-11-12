FROM node:20-alpine

ENV NODE_ENV=production\
    PORT=5000

WORKDIR /app

COPY package*.json ./
RUN npm install --omit=dev && npm cache clean --force

COPY src/ ./src

RUN addgroup -S nodejs && adduser -S nodejs -G nodejs
USER nodejs

EXPOSE 5000

HEALTHCHECK --interval=30s --timeout=30s --start-period=10s --retries=3 CMD wget -qO- http://localhost:5000/health || exit 1

CMD ["npm", "start"]