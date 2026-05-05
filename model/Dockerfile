# Use a slim Python 3.10 image as the base
FROM python:3.10-slim

# Set working directory
WORKDIR /app

# Install system dependencies needed for compiling certain Python packages
RUN apt-get update && apt-get install -y \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

# Copy the requirements file into the container
# Note: You should run the docker build command from the root directory of the project:
# docker build -t nexus-model -f model/Dockerfile .
COPY requirements.txt .

# Install Python dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy the model code into the container
COPY model/ /app/model/

# Set the working directory to the model folder for execution
WORKDIR /app/model

# Define the entrypoint to run the e2e validation script by default
CMD ["python", "run_e2e_validation.py"]
