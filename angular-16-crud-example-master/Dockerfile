# Stage 1: Compile and Build Angular Codebase
FROM node:18.17-alpine as build

# Set the working directory
WORKDIR /usr/src/app

# Copy only the necessary files needed for installing dependencies
COPY package*.json ./

# Install all the dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Generate the build of the application
RUN npm run build
FROM nginx:1-alpine-slim

# Copy the build output to replace the default Nginx contents
COPY --from=build /usr/src/app/dist/angular-16-crud /usr/share/nginx/html

EXPOSE 80

# Health check (optional)
# HEALTHCHECK --interval=30s --timeout=3s CMD wget -q -O /dev/null http://localhost/ || exit 1
