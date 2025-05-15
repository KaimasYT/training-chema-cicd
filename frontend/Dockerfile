FROM node:20-alpine as builder
WORKDIR /app
COPY . .
RUN npm install && npm run build

# Servidor nginx para producción
FROM nginx:stable-alpine
COPY --from=builder /app/dist/* /usr/share/nginx/html/
COPY nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
