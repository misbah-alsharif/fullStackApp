# Step 1: Build Angular app
FROM node:18 AS build
WORKDIR /app

# Copy package.json and install dependencies
COPY package.json ./
RUN npm install

# Copy the rest of the app's source code
COPY . .

# Build the Angular app for production
RUN npm run build --prod

# Step 2: Serve with Nginx
FROM nginx:alpine

# Copy the Angular build to the Nginx server directory
COPY --from=build /app/dist /usr/share/nginx/html

# Expose port 80 for the Nginx server
EXPOSE 80

# Run Nginx in the foreground
CMD ["nginx", "-g", "daemon off;"]
