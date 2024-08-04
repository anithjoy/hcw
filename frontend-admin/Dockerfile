# FROM node:16 AS builder
# WORKDIR /usr/src/app
# COPY package*.json ./
# RUN npm i
# COPY . .
# RUN npx ng build --configuration=production --build-optimizer --aot --output-hashing=all --vendor-chunk

# FROM nginxinc/nginx-unprivileged:latest
# COPY --from=builder /usr/src/app/dist/hug-at-home-admin/ /usr/share/nginx/html/
# COPY nginx-docker.conf.template /etc/nginx/templates/default.conf.template
# COPY nginx.conf /etc/nginx/nginx.conf



FROM node:18
WORKDIR /usr/src/app

COPY package*.json ./
RUN npm i

COPY . .
ENV NODE_OPTIONS=--openssl-legacy-provider
# Install Angular CLI globally
RUN npm install -g @angular/cli

# Expose port 8082 for Angular development server
EXPOSE 8082

# CMD ["npm", "start"]
CMD ["ng", "serve","--configuration", "development", "--host", "0.0.0.0", "--port", "8082"]
# CMD ["ng", "build","--configuration", "development"]

# FROM nginxinc/nginx-unprivileged:latest
# COPY --from=builder /usr/src/app/dist/hug-at-home-admin/ /usr/share/nginx/html/
# COPY nginx-docker.conf.template /etc/nginx/templates/default.conf.template
# COPY nginx.conf /etc/nginx/nginx.conf