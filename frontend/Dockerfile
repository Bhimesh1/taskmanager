# Step 1: Build the app
FROM node:18-alpine AS builder

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .
RUN npm run build

# Step 2: Serve the app with a lightweight web server
FROM nginx:alpine

# Copy built files to nginx
COPY --from=builder /app/dist /usr/share/nginx/html

# Expose port nginx runs on
EXPOSE 5173

CMD ["nginx", "-g", "daemon off;"]
