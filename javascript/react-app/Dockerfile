FROM node:22.8.0 AS builder
WORKDIR /app

COPY --chown=node:node --chmod=644 package*.json ./
RUN npm install

COPY --chown=node:node --chmod=744 . .
RUN npm run build

USER node

FROM nginx:stable-alpine3.20 AS final
WORKDIR /usr/share/nginx/html

COPY --from=builder /app/dist .

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]