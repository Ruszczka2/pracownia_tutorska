# Pracownia Tutorska

Projekt ten obejmuje instalacje i konfiguracje środowiska pod uruchomienie modelu GroundedSAM.

Kod składa się z trzech części:

1. *first_GDSAM.ipynb* -- służy do korzystania z modelu GroundedSAM.
2. *second_creating_dataset.ipynb* -- służy do utworzenia odpowiednego zbioru danych.
3. *third_model.ipynb* -- tworzenie modelu i uczenie maszynowe.

Testy przeprowadzone zostały na WSL 2:
* system operacyjny -- Ubuntu 24.04
* wersja Python -- 3.10
* edytor kodu -- Visual Studio Code

## Instalacja CUDA 12.4

Przy linijce z `cuda-*-keyring.gpg` należy podmienić na kod, który ukaże się podczas instalacji wcześniej
```bash
wget https://developer.download.nvidia.com/compute/cuda/repos/wsl-ubuntu/x86_64/cuda-wsl-ubuntu.pin
sudo mv cuda-wsl-ubuntu.pin /etc/apt/preferences.d/cuda-repository-pin-600
wget https://developer.download.nvidia.com/compute/cuda/12.4.0/local_installers/cuda-repo-wsl-ubuntu-12-4-local_12.4.0-1_amd64.deb
sudo dpkg -i cuda-repo-wsl-ubuntu-12-4-local_12.4.0-1_amd64.deb
sudo cp /var/cuda-repo-wsl-ubuntu-12-4-local/cuda-*-keyring.gpg /usr/share/keyrings/
sudo apt-get update
sudo apt-get -y install cuda-toolkit-12-4
```

Ustawienie ściezki do folderu CUDA
```bash
echo 'export PATH=/usr/local/cuda-12.4/bin:$PATH' >> ~/.bashrc
echo 'export LD_LIBRARY_PATH=/usr/local/cuda-12.4/lib64:$LD_LIBRARY_PATH' >> ~/.bashrc
source ~/.bashrc
```

<!-- Ustawienie stałej ścieżki do folderu z CUDA
```bash
echo 'export CUDA_HOME=/ścieżka/do/cuda' >> ~/.bashrc
```
przykładowo `echo 'export CUDA_HOME=/usr/local/cuda-12.4' >> ~/.bashrc`

Następnie należy sprawdzić czy CUDA_HOME jest ustawiona poprawnie
```bash
source ~/.bashrc
echo $CUDA_HOME
``` -->
<!-- 
Zainstalowanie odpowiedniej wersji pythona
```bash
pyenv install 3.10.13
pyenv local 3.10.13
``` -->

## Instalacja GroundedSAM

Pobranie repozytorium
```bash
git clone https://github.com/Ruszczka2/pracownia_tutorska.git
cd pracownia_tutorska
```

Pobranie python3.10 - Opcjonalne
```bash
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt update
sudo apt install python3.10 python3.10-venv python3.10-dev
```

Zainstalowanie środowiska wirtualnego
```bash
python3.10 -m venv .venv
source .venv/bin/activate
```

Zainstalowanie potrzebnych pakietów
```bash
pip install --upgrade pip
pip install -r requirements.txt
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

<!-- Chyba sys sobie daje rade - sprawdzic
Dodanie Grounded-SAM-2 do ścieżki python
```bash
echo "export PYTHONPATH=\$PYTHONPATH:/pełna/ścieżka/do/Grounded-SAM-2/sam2:/pełna/ścieżka/do/Grounded-SAM-2/grounding_dino" >> ~/.bashrc
source ~/.bashrc
```
przykładowo `echo "export PYTHONPATH=\$PYTHONPATH:/home/ruszczka/projekty/test_files/Grounded-SAM-2/sam2:/home/ruszczka/projekty/test_files/Grounded-SAM-2/grounding_dino" >> ~/.bashrc` -->

<!-- Działa na razie bez tego
Dodanie pliku `__init__.py` do poprawnego działania
```bash
touch /pełna/ścieżka/do/Grounded-SAM-2/grounding_dino/__init__.py
``` 
Przykładowa komenda `touch /home/ruszczka/projekty/test_files/Grounded-SAM-2/grounding_dino/__init__.py`
-->

## Struktura projektu

```
pracownia_tutorska/
├── .venv/                         # Środowisko wirtualne (w .gitignore)
├── .vscode/                       # Folder z potrzebną konfiguracją VSCode 
├── data2/                         # Folder z danymi
├── img/                           # Folder z zdjęciami
├── outputs/                       # Folder przygotowany pod pliki wyjściowe
├── .gitignore                     # Pliki do ignorowania przez Git
├── first_GDSAM.ipynb              # Kod służący do korzystania z modelu GroundedSAM
├── second_creating_dataset.ipynb  # Kod służący do utworzenia odpowiednego zbioru danych
├── third_model.ipynb              # Kod służący do utowrzenia modelu i uczenia maszynowego
├── model_tuned.keras              # Wytrenowany wcześniej model
├── requirements.txt               # Lista potrzebnych pakietów
└── README.md                      # Opis repozytorium
```

## TO-DO

- [ ] Przetestować instalacje na nowym komputerze
- [ ] Sprawdzić, czy działa bez instalacji CUDA
