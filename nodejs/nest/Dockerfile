FROM node:22.8.0 AS builder
WORKDIR /app

COPY --chown=node:node --chmod=644 package*.json ./
RUN npm install

COPY --chown=node:node --chmod=744 . .
RUN npm run build

USER node

FROM node:22.8.0-alpine AS final
USER node
WORKDIR /app

COPY --from=builder /app/package*.json ./
COPY --from=builder /app/node_modules ./node_modules
COPY --from=builder /app/dist ./dist

EXPOSE 3000
CMD ["npm", "run", "start:prod"]