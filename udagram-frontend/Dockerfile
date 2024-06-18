# Use IONIC base image
FROM beevelop/ionic:latest AS ionic

# Create app directory in Docker
WORKDIR /usr/src/app

# Install app dependencies by copying
# package.json and package-lock.json
COPY package*.json ./

# Set environment variable to use legacy OpenSSL provider
ENV NODE_OPTIONS=--openssl-legacy-provider

# Install dependencies in Docker
RUN npm install

# Copy app from local environment into the Docker image
COPY . .

# Build app
RUN ionic build

FROM nginx:alpine

# Copy built app to nginx directory
COPY --from=ionic /usr/src/app/www /usr/share/nginx/html

