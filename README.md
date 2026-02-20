# Coino Node Docker Guide

A comprehensive guide to running a Coino (CNO) v2.0.0 node in a Docker container on modern Linux systems.

## 📦 About This Project

Coino (CNO) is a hybrid cryptocurrency using **X11 (Proof-of-Work) + Proof-of-Stake (PoS)** consensus. Version 2.0.0 was released in June 2017. Despite the absence of public source code for v2.0.0, the Coino network is still alive with about 11 active nodes.

This repository provides:
- ✅ **Detailed instructions** for setting up a Coino node
- ✅ **Ready-to-use Docker image** with all dependencies pre-installed
- ✅ **Working configuration** with active peers
- ✅ **Historical information** about the Coino project

## 🚀 Quick Start

### Option 1: Using the Docker Image (Recommended)

```bash
# 1. Download the Docker image from Releases
wget https://github.com/Serhio2049/coino-node-docker-guide/releases/download/v2.0.0-docker-image/coino-node-docker-image-20260220.tar.gz

# 2. Load the image
gunzip -c coino-node-docker-image-20260220.tar.gz | docker load

# 3. Create data directory
mkdir -p ~/coino-data

# 4. Run the container
docker run -d --name coino-node --restart unless-stopped \
  -v ~/coino-data:/home/coino/_data \
  -p 29293:29293 -p 29299:29299 \
  coino-node:complete-v1 \
  /coino/coino_server/Coinod -conf=/home/coino/config/Coino.conf -datadir=/home/coino/_data

# 5. Check logs
docker logs -f coino-node
