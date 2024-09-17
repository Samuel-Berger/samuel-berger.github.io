--- 
:layout: post
:title: Installation of Jekyll on Fedora
:date: 2023-11-18 00:05:51 +0100
:categories: AI, Docker
---

## Prerequisites

* Working WSL2 distribution.


## Working Docker installation.

On Windows this can be done by running `winget install Docker.DockerDesktop` in Powershell.
You probably need to reboot the computer or at least log out and log in.
Then open Docker Desktop and make sure that WSL2-integration is activated.
You might need to add your WSL-user to the docker group and adjust some permissions.
Do that by running (in your WSL enviroment, probably Bash):

``sh
sudo usermod -aG docker $USER
ls -l /var/run/docker.sock
sudo chmod 666 /var/run/docker.sock
``

## Run Ollama Via Docker

Ollama helps you test differend AI models on the machine of your choice and is
[now available as a docker image](https://ollama.com/blog/ollama-is-now-available-as-an-official-docker-image).
In the WSL2 distribution of your choice run

```sh
docker run -d -v ollama:/root/.ollama -p 11434:11434 --name ollama ollama/ollama
```

Once Ollama is downloaded and started visit <locallhost:11434> and make sure you get the greeting "Ollama is running".

## Make NVIDIA GPU available to Docker

Remove or rename the previously installed Docker image. Then follow the [installation instructions](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html#installing-with-apt). Test run with `sudo docker run --rm --runtime=nvidia --gpus all ubuntu nvidia-smi`

## Run a Local LLM

As a [note states](https://github.com/ollama/ollama): "You should have at least 8 GB of RAM available to run the 7B models, 16 GB to run the 13B models, and 32 GB to run the 33B models".

You can see amount of avaialbe ram in WSL with `free -h`. There is also the option to
[increase the memory limits]( https://fizzylogic.nl/2023/01/05/how-to-configure-memory-limits-in-wsl2) for WSL2.

1. Make sure Ollama is running by visiting <locallhost:11434>. 
2. Choose a model [from the library](https://ollama.com/library).
3. Run the model with `docker exec -it ollama ollama run [libraryname]` for example
`docker exec -it ollama ollama run llama2`


## Example Code and the Matching Models

There are examples available for
[Python](https://github.com/ollama/ollama-python/blob/main/examples/tools/main.py)
and [Javascript](https://github.com/ollama/ollama-js).
Below the [Javascript examples](https://github.com/ollama/ollama-js/blob/main/examples/tools/tools.ts) are used.

```sh
git clone https://github.com/ollama/ollama-js.git
# Add "type": "module", to package.json
 cd ollama-js/examples/
pnpm install
pnpm run build
cd examples
pnpx tsx abort/any-request.ts   # Need llama3.1
# Analyzes pictures and need llava
pnpx tsx multimodal/multimodal.ts
pnpx tsx tools/tools.ts # 
```

