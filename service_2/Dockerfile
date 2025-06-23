FROM python:3.13-slim

# Install uv and system dependencies
RUN apt-get update && apt-get install -y curl build-essential && \
    curl -LsSf https://astral.sh/uv/install.sh | sh && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# Add uv to PATH
ENV PATH="/root/.local/bin:$PATH"

# Set working directory
WORKDIR /app

# Copy app source
COPY . .

# Install flask system-wide (no venv)
RUN uv pip install flask --system

EXPOSE 8002

CMD ["python", "app.py"]
