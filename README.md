# AI-Days 2025 - RAG Workshop

## Exoscale setup
Exoscale setup for GPUs instances :

- Install the nivdia drivers... : sudo apt-get install nvidia-driver-565-server -y
- Check the nvidia driver version : sudo nvidia-smi -L
- Install docker following the steps [here](https://docs.docker.com/engine/install/ubuntu/)
- Install the nvidia container toolkit following the steps [here](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html#installing-with-apt)
- Reboot the instance

Don't forget to add a rule to allow the port 11434 in the security group of the instance.

/!\ Ollama do not provide authentication by default, for a production environment you should add a reverse proxy with authentication.

## Ollama commands

`sudo docker run -d --restart=unless-stopped --gpus=all -p 11434:11434 --name ollama-gpu -e OLLAMA_NUM_PARALLEL=4 -e OLLAMA_MAX_LOADED_MODELS=4 ollama/ollama`

`sudo docker exec -it ollama-gpu ollama pull qwen2.5:0.5b`

`sudo docker logs -f ollama-gpu`

Ollama website: https://ollama.com/

qwen2.5 model: https://ollama.com/library/qwen2.5:0.5b
