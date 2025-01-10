# rag-workshop

Setup exoscale for GPUs instances :

- Install the nivdia drivers... : sudo apt-get install nvidia-driver-565-server -y
- Check the nvidia driver version : sudo nvidia-smi -L
- Install docker following the steps [here](https://docs.docker.com/engine/install/ubuntu/)
- Install the nvidia container toolkit following the steps [here](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html#installing-with-apt)
- reboot the instance

Don't forget to add a rule to allow the port 11434 in the security group of the instance.

## Ollama commands

`sudo docker run -d --restart=unless-stopped --gpus=all -p 11434:11434 --name ollama-gpu -e OLLAMA_NUM_PARALLEL=4 -e OLLAMA_MAX_LOADED_MODELS=4 ollama/ollama`

`sudo docker exec -it ollama-gpu ollama run gemma`

`sudo docker logs -f ollama-gpu`
