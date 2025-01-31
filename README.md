# Local DeepSeek-R1 Setup with Ollama and Open WebUI

This repository provides a step-by-step guide to running DeepSeek-R1 locally on your PC using Ollama and Open WebUI. The setup involves installing Ollama on Windows 10 WSL (Ubuntu 24.04.1 LTS) and running Open WebUI inside a Docker container.

## Prerequisites

- Windows 10 with WSL 2 installed
- Docker installed on Windows
- Ubuntu 24.04.1 LTS installed on WSL

## Step 1: Install Ollama on WSL

1. Open your WSL terminal (Ubuntu 24.04.1 LTS).
2. Run the following command to install Ollama:

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

3. Verify the installation by checking the Ollama version:

```bash
ollama --version
```

You should see something like `ollama version 0.5.7`.

## Step 2: Pull and Run Open WebUI Docker Image

1. Open PowerShell on your Windows machine.
2. Run the following Docker command to pull and run the Open WebUI image:

```powershell
docker run -d -p 3000:8080 --add-host=host.docker.internal:host-gateway -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:main
```

   This command will:
   - Run the Open WebUI container in detached mode (`-d`).
   - Map port 3000 on your local machine to port 8080 in the container (`-p 3000:8080`).
   - Add a host entry for `host.docker.internal` (`--add-host=host.docker.internal:host-gateway`).
   - Create a volume for persistent data storage (`-v open-webui:/app/backend/data`).
   - Name the container `open-webui` (`--name open-webui`).
   - Ensure the container restarts always (`--restart always`).

3. Verify that the container is running by checking Docker logs or using `docker ps`.

## Step 3: Access Open WebUI

1. Open your web browser and navigate to `http://localhost:3000`.
2. You should see the Open WebUI interface.

## Step 4: Test DeepSeek-R1

1. In the Open WebUI, create a new chat.
2. Select the `deepseek-r1:1.5b` model.
3. Start interacting with the model by asking questions or requesting code snippets.

## Screenshots

Here are some screenshots of the setup and testing process:

- [Ollama Installation on WSL](ollama-wsl-ubuntu-24.04.1-lts-terminal.png)
- [Running Open WebUI Docker Container](ollama-open-webui-docker.png)
- [Open WebUI Interface](open-webui-deepseek.png)
- [Sign In to Open WebUI](open-webui-deepseek-r1-1.5b.png)
- [Chatting with DeepSeek-R1](open-webui-deepseek-r1-1.5b-chat-1.png)
- [DeepSeek-R1 Response](open-webui-deepseek-r1-1.5b-chat-2.png)

## Conclusion

You have successfully set up DeepSeek-R1 locally using Ollama and Open WebUI. This setup allows you to interact with the DeepSeek-R1 model directly from your local machine.

For more information, visit the official DeepSeek documentation:
- [DeepSeek Official Website](https://www.deepseek.com)
- [DeepSeek-R1 Release](https://api-docs.deepseek.com/news/news250120)
