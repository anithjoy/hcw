# FROM node:18 AS builder
# WORKDIR /usr/src/app
# COPY package*.json ./
# COPY yarn.lock ./
# RUN npx yarn install
# COPY . .
# #RUN npx ng build --configuration=production --build-optimizer --aot --output-hashing=all --vendor-chunk
# RUN make

# FROM nginxinc/nginx-unprivileged:latest
# COPY --from=builder /usr/src/app/dist/hug-at-home/ /usr/share/nginx/html/
# COPY nginx-docker.conf.template /etc/nginx/templates/default.conf.template
# COPY nginx.conf /etc/nginx/nginx.conf
# #RUN sed -i  's/\(default_type.*\)/\1\n    proxy_headers_hash_bucket_size 128;/g' /etc/nginx/nginx.conf




# Use the Node.js 18 image
FROM node:18

# Set the working directory
WORKDIR /usr/src/app

# Copy the package.json and yarn.lock files
COPY package*.json ./
COPY yarn.lock ./

# Install the dependencies
RUN yarn install

# Copy the application files
COPY . .

# Install Angular CLI globally
RUN yarn global add @angular/cli

# Expose port 8081 for the Angular development server
EXPOSE 8081

# Start the Angular development server
CMD ["ng", "serve", "--host", "0.0.0.0", "--port", "8081"]
