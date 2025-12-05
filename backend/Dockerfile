FROM node:18-alpine

# Thư mục làm việc trong container
WORKDIR /app

# Copy file package để cài dependency trước (tối ưu cache)
COPY package*.json ./

# Cài dependency ở chế độ production
RUN npm install --production

# Copy source code còn lại
COPY . .

# Biến môi trường mặc định (có thể override từ K8s)
ENV NODE_ENV=production

# Container lắng nghe port 5001 (giống PORT trong .env)
EXPOSE 5001

# Lệnh chạy app (trùng "start": "node src/server.js")
CMD ["node", "src/server.js"]
