# Base Image
# python<version>-slim/bullseye/alpine based on your requirement
FROM python:3.9-slim

LABEL author="Pradeep Tarakar"

# Set env vars
ENV USER=app

# Create and set a user
RUN useradd -m ${USER}
USER ${USER}  

# Set working directory to user dir
WORKDIR /home/${USER}

# Copy requirements.toml
COPY --chown=${USER} requirements.txt .

# Add pip installation path to PATH
ENV PATH="/home/${USER}/.local/bin:$PATH"

# Install deps from requirements.txt
RUN pip install --no-cache-dir --upgrade -r requirements.txt

# Copy project files (in this case it is a single file Experiment1.py)
COPY --chown=${USER} Experiment1.py .

# Expose required port
EXPOSE 8080

# Entrypoint
CMD [ "uvicorn", "Experiment1:app", "--host", "0.0.0.0", "--port", "8080" ]
