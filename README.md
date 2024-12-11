# rag-workshop

Setup lambdalabs instance 1 day before the workshop.

## Ollama commands

`sudo docker run -d --restart=unless-stopped --gpus=all -p 11434:11434 --name ollama-gpu -e OLLAMA_NUM_PARALLEL=4 -e OLLAMA_MAX_LOADED_MODELS=4 ollama/ollama`

`sudo docker exec -it ollama-gpu ollama run gemma`

`sudo docker logs -f ollama-gpu`
