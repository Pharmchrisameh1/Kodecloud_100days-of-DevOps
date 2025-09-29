# Use Python base image
FROM python:3.9-slim

# Set working directory
WORKDIR /app

# Copy and install dependencies
COPY src/requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy application files
COPY src/ .

# Expose port
EXPOSE 8085

# Start the app
CMD ["python", "server.py"]

