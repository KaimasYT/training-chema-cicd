# Etapa 1: build con Node.js
FROM node:20-alpine AS builder

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

RUN npm run build

# Etapa 2: usar Nginx para servir
FROM nginx:stable-alpine

# Elimina la página por defecto
RUN rm -rf /usr/share/nginx/html/*

# Copia archivos de build al directorio de Nginx
COPY --from=builder /app/dist /usr/share/nginx/html

# Copia configuración custom si tienes una
# COPY nginx.conf /etc/nginx/nginx.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]

