# Dockerfile

# Use official Python image as a base
FROM python:3.11-slim

# Set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# Set the working directory in the container
WORKDIR /app

RUN apt-get update \
    && apt-get install -y \
    binutils \
    libproj-dev \
    gdal-bin \
    libgdal-dev \
    && rm -rf /var/lib/apt/lists/*

# Set the environment variable for GDAL
ENV GDAL_LIBRARY_PATH=/usr/lib/x86_64-linux-gnu/gdal

# Install dependencies
COPY requirements.txt /app/
RUN pip install --no-cache-dir -r requirements.txt

# Copy the project files
COPY . /app/

# Run Django development server
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]