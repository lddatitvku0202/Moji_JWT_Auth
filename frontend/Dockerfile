# Stage 1: build React app
FROM node:18-alpine AS build

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .
RUN npm run build

# Stage 2: serve bằng Nginx
FROM nginx:alpine

# Copy file cấu hình Nginx custom
COPY nginx.conf /etc/nginx/nginx.conf

# Copy static build sang thư mục Nginx
COPY --from=build /app/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
