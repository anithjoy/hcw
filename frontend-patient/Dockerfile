FROM node:18.18 AS builder
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm i
COPY . .
RUN npx ionic cap build browser --prod --no-open

FROM nginxinc/nginx-unprivileged:latest
COPY --from=builder /usr/src/app/www/ /usr/share/nginx/html/
COPY nginx-docker.conf.template /etc/nginx/templates/default.conf.template
COPY nginx.conf /etc/nginx/nginx.conf
USER 0
RUN apt-get update && \
  apt install -y jq && \
  rm -rf /var/lib/apt/lists/*
USER 101



# # Use the Node.js 18 image
# FROM node:18.18

# # Set the working directory
# WORKDIR /usr/src/app

# # Copy the package.json and package-lock.json files
# COPY package*.json ./

# # Install the dependencies
# RUN npm install

# # Copy the application files
# COPY . .

# # Install Ionic CLI globally
# RUN npm install -g @ionic/cli

# # Expose port 8080 for the Ionic development server
# EXPOSE 8080

# # Start the Ionic development server
# CMD ["ionic", "serve", "--host", "0.0.0.0", "--port", "8080"]
