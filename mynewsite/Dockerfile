# # Use an official Hugo image as the base image
# FROM klakegg/hugo:0.101.0-alpine

# # Set the working directory inside the container
# WORKDIR /src

# # Copy the Hugo site source files to the container
# COPY . .

# # Build the Hugo site
# RUN hugo

# # Expose the port that Hugo serves the site on (default is 1313)
# EXPOSE 1313

# # Start the Hugo server
# # CMD ["hugo", "server", "--bind", "0.0.0.0"]

# FROM alpine:3.5 as build

# FROM klakegg/hugo:0.101.0-alpine as build

# COPY ./ /site

# WORKDIR /site

# RUN hugo

# FROM nginx:alpine

# LABEL maintainer Eduardo Reyes <eduardo@reyes.im>

# COPY ./conf/default.conf /etc/nginx/conf.d/default.conf

# COPY --from=build /site/public /var/www/site

# WORKDIR /var/www/site

# # Expose port 80
# EXPOSE 80/tcp


# Stage 1: Build the Hugo website
FROM klakegg/hugo:0.88.1 AS builder
WORKDIR /app
COPY . .
RUN hugo

# Stage 2: Serve the Hugo website using Nginx
FROM nginx:latest
COPY --from=builder /app/public /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
