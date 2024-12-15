# Stage 1: Build Stage
FROM node:20 AS build
WORKDIR /app

# Install dependencies
COPY package.json package-lock.json ./
RUN npm install

# Copy source code and build
COPY . .
RUN npm run build

# Stage 2: Serve Stage
FROM nginx:stable-alpine
COPY --from=build /app/dist /usr/share/nginx/html

# Expose port 80 and start NGINX
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
