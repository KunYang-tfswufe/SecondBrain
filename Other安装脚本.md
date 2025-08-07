```bash
# https://github.com/Jguer/yay/
  sudo pacman -Syu
  sudo pacman -S git
  git clone https://aur.archlinux.org/yay.git
  cd yay
  makepkg -si
# https://github.com/docker
  sudo pacman -S docker docker-compose    
  sudo systemctl start docker
  sudo systemctl enable docker
  sudo usermod -aG docker $USER
  sudo poweroff
# https://github.com/espanso
  yay -S espanso-wayland
  espanso service register
  espanso service start
# https://github.com/fish-shell/fish-shell
  sudo pacman -S fish
  chsh -s /usr/bin/fish
# https://www.qemu.org
  sudo pacman -S qemu-full edk2-ovmf
# https://github.com/Mintplex-Labs/anything-llm
  docker pull mintplexlabs/anythingllm
  docker run -d --restart always -p 3001:3001 mintplexlabs/anythingllm  
# https://github.com/open-webui/open-webui
  docker run -d -p 3000:8080 --add-host=host.docker.internal:host-gateway -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:main  
# https://github.com/danielgatis/rembg
  docker run -d --restart always -p 7000:7000 danielgatis/rembg s --host 0.0.0.0 --port 7000
# https://github.com/ollama/ollama
  sudo pacman -S ollama-cuda
  sudo systemctl enable ollama
  sudo systemctl start ollama
```