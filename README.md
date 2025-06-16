# Pracownia Tutorska

--- opis ---

## Przed instalacją

--- pobranie CUDA ---

Ustawienie stałej ścieżki do folderu z CUDA
```bash
echo 'export CUDA_HOME=/ścieżka/do/cuda' >> ~/.bashrc
```
przykładowo `echo 'export CUDA_HOME=/usr/local/cuda-12.4' >> ~/.bashrc`

Następnie należy sprawdzić czy CUDA_HOME jest ustawiona poprawnie
```bash
source ~/.bashrc
echo $CUDA_HOME
```


## Instalacja

Pobranie repozytorium
```bash
git clone https://github.com/Ruszczka2/pracownia_tutorska.git
cd pracownia_tutorska
```

Zainstalowanie środowiska wirtualnego
```bash
python3 -m venv .venv
source .venv/bin/activate
```

Zainstalowanie potrzebnych pakietów
```bash
pip3 install -r rquirements.txt
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
├──
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