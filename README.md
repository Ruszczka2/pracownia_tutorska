# Pracownia Tutorska

--- opis ---

## Przed instalacją

Instalacja CUDA 11.8
```bash
wget https://developer.download.nvidia.com/compute/cuda/repos/wsl-ubuntu/x86_64/cuda-wsl-ubuntu.pin
sudo mv cuda-wsl-ubuntu.pin /etc/apt/preferences.d/cuda-repository-pin-600
wget https://developer.download.nvidia.com/compute/cuda/11.8.0/local_installers/cuda-repo-wsl-ubuntu-11-8-local_11.8.0-1_amd64.deb
sudo dpkg -i cuda-repo-wsl-ubuntu-11-8-local_11.8.0-1_amd64.deb
sudo cp /var/cuda-repo-wsl-ubuntu-11-8-local/cuda-*-keyring.gpg /usr/share/keyrings/
sudo apt-get update
sudo apt-get -y install cuda
```

Ustawienie stałej ścieżki do folderu z CUDA
```bash
echo 'export CUDA_HOME=/ścieżka/do/cuda' >> ~/.bashrc
```
przykładowo `echo 'export CUDA_HOME=/usr/local/cuda-11.8' >> ~/.bashrc`

Następnie należy sprawdzić czy CUDA_HOME jest ustawiona poprawnie
```bash
source ~/.bashrc
echo $CUDA_HOME
```
<!-- 
Zainstalowanie odpowiedniej wersji pythona
```bash
pyenv install 3.10.13
pyenv local 3.10.13
``` -->

!! Sprawdzić czy nie trzeba pobrać python 3.10 przed !!

## Instalacja

Pobranie repozytorium
```bash
git clone https://github.com/Ruszczka2/pracownia_tutorska.git
cd pracownia_tutorska
```

Zainstalowanie środowiska wirtualnego
```bash
python3.10 -m venv .venv
source .venv/bin/activate
```

Zainstalowanie potrzebnych pakietów
```bash
pip3 install --upgrade pip
pip3 install -r requirements.txt
```

Pobranie z Github GroundedSAM
```bash
git clone https://github.com/IDEA-Research/Grounded-SAM-2.git
cd Grounded-SAM-2
```

Pobranie konfiguracji SAM
```bash
cd checkpoints
bash download_ckpts.sh
cd ..
```

Pobranie konfiguracji GDINO
```bash
cd gdino_checkpoints
bash download_ckpts.sh
cd ..
```

Instalacja SAM
```bash
pip install -e .
```

Instalacja GDINO
```bash
pip install --no-build-isolation -e grounding_dino
```

<!-- Dodanie Grounded-SAM-2 do ścieżki python
```bash
echo "export PYTHONPATH=\$PYTHONPATH:/pełna/ścieżka/do/Grounded-SAM-2/sam2:/pełna/ścieżka/do/Grounded-SAM-2/grounding_dino" >> ~/.bashrc
source ~/.bashrc
```
przykładowo `echo "export PYTHONPATH=\$PYTHONPATH:/home/ruszczka/projekty/test_files/Grounded-SAM-2/sam2:/home/ruszczka/projekty/test_files/Grounded-SAM-2/grounding_dino" >> ~/.bashrc` -->

Dodanie pliku `__init__.py` do poprawnego działania
```bash
touch /pełna/ścieżka/do/Grounded-SAM-2/grounding_dino/__init__.py
```
Przykładowa komenda `touch /home/ruszczka/projekty/test_files/Grounded-SAM-2/grounding_dino/__init__.py`

## Struktura projektu

```
twoj-projekt/
├── .venv/                 # Środowisko wirtualne (w .gitignore)
├── .vscode/               # Folder z potrzebną konfiguracją VSCode 
├── data2/                 # Folder z danymi
├── img/                   # Folder z zdjęciami
├──
├──
├── requirements.txt       # Lista zależności
└── README.md              # Ten plik
```

## To-DO

- [ ] Uzupełnić opis
- [ ] Uzupełnić strukturę projektu
- [ ] Uzupełnić nagłówek *Przed instalacją*
- [x] Sprawdzenie listy ToDo
- [ ] Upewnić się czy trzeba pobrać dodatkowo python 3.10