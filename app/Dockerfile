# Use lightweight base image
FROM python:3.11-slim

# Create a non-root user
RUN useradd -m appuser

# Set working directory
WORKDIR /app

# Copy requirements first (for caching)
COPY requirements.txt .

# Install dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy app code
COPY app.py .

# Change ownership to non-root user
RUN chown -R appuser:appuser /app

# Switch to non-root user
USER appuser

# Expose port
EXPOSE 5000

# Run app using gunicorn (recommended)
CMD ["python", "app.py"]
