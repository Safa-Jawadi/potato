# # Stage 1: Development
# FROM node:lts as development
# WORKDIR /home/node/app
# # Copy package.json and package-lock.json first to leverage Docker caching
# COPY package*.json ./
# # Install dependencies for development
# RUN npm install

# Stage 2: Production
FROM node:lts as production
WORKDIR /home/node/app
# Copy package.json and package-lock.json first to leverage Docker caching
COPY package*.json ./
# Install only production dependencies
RUN npm install --production
# Copy source code
COPY --chown=node:node . .
# Build the Docusaurus app
RUN npm run build

# Stage 3: Deploy
FROM nginx:stable-alpine as deploy
WORKDIR /usr/share/nginx/html
# Copy built files from the production stage
COPY --from=production /home/node/app/build .
