# frontend/Dockerfile

# Etapa de construcción
FROM node:18-alpine as build
WORKDIR /app
COPY . .
RUN npm install
RUN npm run build -- --output-path=dist

# Etapa de producción
FROM nginx:alpine
COPY --from=build /app/dist /usr/share/nginx/html
