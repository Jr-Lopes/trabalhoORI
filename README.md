sudo pacman -Syu --needed fio git python python-pip libjpeg-turbo

cd ~
git clone https://github.com/louwrentius/fio-plot.git
cd fio-plot
source venv/bin/activate.fish
pip install fio-plot

mkdir -p ~/temp
bench-fio --target ~/temp --type directory --size 2G --mode randread --output MeuPC --iodepth 1 8 32 --numjobs 1 4

fio-plot -i MeuPC/temp/4k/ -T "Performance de Leitura - Kingston SNV2S" -l -r randread -d 1 8 32 -n 1

fio-plot -i MeuPC/temp/4k/ -T "IOPS vs Latencia (Agrupado) - Kingston SNV2S" -l -r randread -d 1 8 32 -n 1 --group-bars

fio-plot -i MeuPC/temp/4k/ -T "Latencia 3D - Kingston SNV2S" -L -t lat -r randread -d 1 8 32 -n 1 4

xdg-open .
