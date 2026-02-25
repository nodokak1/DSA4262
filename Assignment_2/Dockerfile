FROM python:3.11-slim

WORKDIR /app

# Environment variables you already use in notebook
ENV NUMBA_DISABLE_JIT=1 \
    TOKENIZERS_PARALLELISM=false \
    MPLCONFIGDIR=/app/.mplconfig

# Basic OS deps that help scientific wheels and text libs
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    git \
    && rm -rf /var/lib/apt/lists/*

# Install Python deps
COPY requirements.txt .
RUN pip install --upgrade pip && pip install -r requirements.txt

# Copy your assignment files
COPY . .

EXPOSE 8888
CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--allow-root"]