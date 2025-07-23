# syntax=docker/dockerfile:1
FROM python:3.10-alpine

# Set working directory inside container
WORKDIR /code

# Flask environment variables
ENV FLASK_APP=app.py
ENV FLASK_RUN_HOST=0.0.0.0
ENV FLASK_RUN_PORT=5000

# Ensure user-installed packages are available
ENV PATH="/root/.local/bin:$PATH"

# Install required system dependencies
RUN apk add --no-cache \
    gcc \
    musl-dev \
    linux-headers \
    libffi-dev \
    python3-dev \
    py3-pip

# Install Python dependencies (user install)
COPY requirements.txt .
RUN pip install --no-cache-dir --user -r requirements.txt

# Copy application code
COPY . .

# Expose Flask port
EXPOSE 5000

# Start Flask app using shell form
CMD flask run --debug