# Setting Up a Vector Database (ChromaDB) with Docker

## Objective

Set up and configure ChromaDB—a vector database—using Docker to efficiently store and manage vector embeddings.

## Overview

This guide will help you:

- Pull the ChromaDB Docker image.
- Create and configure a ChromaDB container.
- Ensure seamless interaction with your Python environment in Jupyter Notebook.

This setup will serve as the foundation for storing and retrieving vector embeddings in subsequent tasks.

## Steps to Deploy ChromaDB Using Docker

1. **Pull the ChromaDB Docker Image**

   ```bash
   docker pull chromadb/chroma:0.5.13
   ```

2. **Run the ChromaDB Container**

Execute following command in the shell path: `~/build-your-own-chatbot`:

  ```bash
  docker run -d \
    -p 8000:8000 \
    -v "$(pwd)/container_cache/chroma:/chroma/chroma" \
    -e IS_PERSISTENT=TRUE \
    -e PERSIST_DIRECTORY=./chroma/chroma \
    chromadb/chroma:0.5.13
  ```

   - **Flags and Environment Variables:**
     - `-v [local_dir]:[container_dir]`: Mounts a local directory to the container. This is where ChromaDB will store its data, ensuring data persistence even if the container is destroyed.
     - `-e IS_PERSISTENT=TRUE`: Instructs ChromaDB to persist data.
     - `-e PERSIST_DIRECTORY=/path/in/container`: Specifies the path inside the container where data will be stored. The default is `/chroma/chroma`.
     - `chromadb/chroma:latest`: Specifies the ChromaDB version. Replace `latest` with a specific tag if you need a prior version (e.g., `chromadb/chroma:0.5.13`).

## Notes

- **Port Mapping (`-p 8000:8000`):** Exposes ChromaDB on port `8000`. Ensure this port is available and not blocked by a firewall.
- **Data Persistence:** Using the `-v` flag with a local directory ensures that your data remains intact even if the Docker container is removed.
- **Environment Variables:** Adjust the `IS_PERSISTENT` and `PERSIST_DIRECTORY` variables based on your requirements.