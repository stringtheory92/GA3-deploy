# Stage 1: Build the app
FROM node:16 AS build

# Set working directory
WORKDIR /app

# Copy package.json and install dependencies
COPY ./package.json ./
RUN npm install

# Copy the rest of the app source code
COPY . .

# Build the React app
RUN npm run build

# Stage 2: Serve the app using an Nginx server
FROM nginx:alpine

# Copy the build output to Nginx's HTML directory
COPY --from=build /app/build /usr/share/nginx/html

# Expose port 3001
EXPOSE 3001

# Run Nginx
CMD ["nginx", "-g", "daemon off;"]
