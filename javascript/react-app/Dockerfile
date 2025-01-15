FROM node:22.8.0 AS builder
LABEL owner="JvictorMarques"
RUN groupadd -r app && useradd -r -g app app
WORKDIR /app

COPY --chown=app:app --chmod=644 package*.json ./
RUN npm install

COPY --chown=app:app --chmod=744 . .
RUN npm run build

USER app

FROM nginx:alpine AS final
WORKDIR /usr/share/nginx/html

COPY --from=builder /app/dist .

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]