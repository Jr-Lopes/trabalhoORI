# ?? Benchmark de Desempenho de SSD: WSL2 vs. CachyOS (Nativo)

Este repositório contém a metodologia, scripts, imagens e a apresentação do estudo comparativo de desempenho de E/S (Input/Output) do SSD **Kingston SNV2S**, avaliando o impacto do overhead de virtualização do **WSL2 (Windows 11)** em relação ao ambiente bare-metal **Linux CachyOS**.

---

## ??? Requisitos e Instalação (CachyOS / Arch Linux)

Para reproduzir os testes e a geração dos gráficos de desempenho, instale as dependências de sistema e a ferramenta fio-plot:

`ash
# Instalação das dependências do sistema
sudo pacman -Syu --needed fio git python python-pip libjpeg-turbo

# Clonagem do repositório do fio-plot e instalação
cd ~
git clone [https://github.com/louwrentius/fio-plot.git](https://github.com/louwrentius/fio-plot.git)
cd fio-plot
source venv/bin/activate.fish
pip install fio-plot
