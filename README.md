# Configurações na máquina local (para sistemas "Debian based" com NVIDIA)

Estas configurações são necessárias para fazer o transcoding de vídeos utilizando o NVENC. Sem isso, o container não consegue enxergar a placa de vídeo.

**1. Instalar a chave GPG do repositório da NVIDIA:**
```
sudo mkdir -p /usr/share/keyrings
curl -fsSL https://nvidia.github.io/libnvidia-container/gpgkey \
 | sudo gpg --dearmor -o /usr/share/keyrings/nvidia-container-toolkit-keyring.gpg
```

**2. Adicionar o repositório da NVIDIA ao APT:**
```
echo "deb [signed-by=/usr/share/keyrings/nvidia-container-toolkit-keyring.gpg] https://nvidia.github.io/libnvidia-container/stable/deb/amd64 /" \
 | sudo tee /etc/apt/sources.list.d/nvidia-container-toolkit.list
```

**3. Instalar container com o toolkit da NVIDIA:**
```
sudo apt update
sudo apt install -y nvidia-container-toolkit
```

Após isso, basta subir o composer do Jellyfin:
```
docker compose up
```
