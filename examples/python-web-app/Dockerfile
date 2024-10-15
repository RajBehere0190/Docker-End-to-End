# Use the official Ubuntu as the base image
FROM ubuntu

# Set the working directory
WORKDIR /app

# Copy the requirements file and devops folder into the container
COPY requirements.txt /app/
COPY devops /app/devops/

# Install dependencies
RUN apt-get update && \
    apt-get install -y python3 python3-pip python3-venv gcc && \
    rm -rf /var/lib/apt/lists/*

# Create a virtual environment and install Python dependencies
RUN python3 -m venv /opt/venv && \
    /opt/venv/bin/pip install --upgrade pip && \
    /opt/venv/bin/pip install --no-cache-dir -r /app/requirements.txt

# Ensure the virtual environment is used for subsequent commands
ENV PATH="/opt/venv/bin:$PATH"

# Set the working directory to devops directly
WORKDIR /app/devops

# Set the entry point for the Docker container
ENTRYPOINT ["python3"]
CMD ["manage.py", "runserver", "0.0.0.0:8000"]
