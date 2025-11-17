# =============================
# 1. Base Image
# =============================
FROM ubuntu:22.04

# Prevent interactive prompts
ENV DEBIAN_FRONTEND=noninteractive

# =============================
# 2. System Dependencies
# =============================
RUN apt-get update && apt-get install -y \
    curl \
    python3 \
    python3-pip \
    python3-venv \
    git \
    && rm -rf /var/lib/apt/lists/*

# =============================
# 3. Install Ollama
# =============================
RUN curl -fsSL https://ollama.com/install.sh | sh

# =============================
# 4. Pull Qwen model (3B VL)
# =============================
RUN ollama pull qwen2.5vl:3b

# =============================
# 5. Working Directory
# =============================
WORKDIR /app


# 6. Copy project code (SRC) and requirements
# IMPORTANT: Build context must be project root
# =============================
# Copy the whole src folder so imports like `from src.models ...` work
COPY src /app/src

# Copy root-level requirements.txt
COPY requirements.txt /app/requirements.txt


# =============================
# 6. Python Packages
# =============================
# Install Python dependencies
RUN pip install --no-cache-dir -r /app/requirements.txt

# =============================
# 7. Expose FastAPI port
# =============================
EXPOSE 8000

# =============================
# 8. Start Ollama + FastAPI together
# =============================
CMD ollama serve & uvicorn main:app --host 0.0.0.0 --port 8000
