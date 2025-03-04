# Use official Nginx base image (Alpine for lightweight)
FROM nginx:latest

# Remove default Nginx configuration
RUN rm /etc/nginx/conf.d/default.conf
RUN rm /etc/nginx/nginx.conf

# Copy custom Nginx configuration
COPY ./conf.d/api-gateway.conf /etc/nginx/conf.d/api-gateway.conf
COPY nginx.conf /etc/nginx/nginx.conf
# Set working directory (optional, for clarity)
WORKDIR /etc/nginx

# Expose port 80 (HTTP)
EXPOSE 80

# Healthcheck (optional, for production readiness)
HEALTHCHECK --interval=30s --timeout=3s \
  CMD curl -f http://localhost/ || exit 1

# Start Nginx in the foreground (default behavior)
CMD ["nginx", "-g", "daemon off;"]