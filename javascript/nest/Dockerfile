FROM node:22.8.0 AS builder
WORKDIR /app

COPY --chown=node:node package*.json ./
RUN npm install

COPY --chown=node:node . .
RUN npm run build

USER node

FROM node:22.8.0-alpine AS final
WORKDIR /app

USER node

COPY --from=builder /app/dist ./dist

EXPOSE 3000
CMD ["npm", "run", "start:prod"]