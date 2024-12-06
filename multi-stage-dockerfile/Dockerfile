# Stage 1: Build Stage
FROM python:3.10-slim as builder

# Set the working directory
WORKDIR /app

# Copy only the requirements file to leverage Docker's caching mechanism
COPY ./requirements.txt /app/requirements.txt

# Install build dependencies
RUN apt-get update && apt-get install -y --no-install-recommends build-essential && \
    python -m venv /venv && \
    /venv/bin/pip install --no-cache-dir -r requirements.txt && \
    apt-get purge -y --auto-remove build-essential && \
    rm -rf /var/lib/apt/lists/*

# Install project dependencies
RUN mkdir /app/static && mkdir /app/templates

# Stage 2: Runtime Stage
FROM python:3.10-alpine

# Set environment variables
ENV PATH="/venv/bin:$PATH" \
    FLASK_ENV=production

# Set the working directory
WORKDIR /app

# Copy application code
COPY . /app

# Copy the virtual environment from the build stage
COPY --from=builder /venv /venv

# Expose the Flask app's port
EXPOSE 5000

# Define the command to run the Flask app
CMD ["flask", "run", "--host=0.0.0.0", "--port=5000"]

