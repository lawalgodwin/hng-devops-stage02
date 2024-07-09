# Use Node:alpine as the base image for build
FROM node:alpine AS build

# Set the working directory
WORKDIR /usr/src/app
# Set up the build environment
COPY package.json package-lock.json ./
COPY tsconfig.json tsconfig.json
COPY tsconfig.node.json tsconfig.node.json
COPY vite.config.ts vite.config.ts
RUN npm install
# Copy application code
COPY . .
# Get the api url
# ARG VITE_API_URL=${VITE_API_URL}
# Build the application
RUN npm run build

# -----------------------------------------------------------------
# Create a production image
# -------------------------------------------------------------------
FROM nginx AS production

# Copy static files from the build stage
COPY --from=build /usr/src/app/dist /usr/share/nginx/html
# override the default config file in nginx
COPY nginx.conf /etc/nginx/conf.d/default.conf