# ☕ Classificador de torra com YOLO e CNN

Este projeto utiliza **YOLO** para detectar grãos de café em imagens e uma **CNN** para classificar o nível de torra (clara, média ou escura). O objetivo é criar um sistema eficiente e automatizado para análise de grãos com aplicação em qualidade de produção.

---

## 📁 Estrutura do Projeto

### `data/`
Contém todos os dados usados no projeto, desde imagens brutas até os dados prontos para treino.

- `raw/`: Imagens originais dos grãos de café, sem anotações.
- `yolov8/`: Dataset anotado no formato YOLO (pasta `images/` e `labels/`).
- `crops/`: Recortes individuais de grãos detectados pelo YOLO.
- `cnn/`: Imagens recortadas organizadas por tipo de torra:

### `models/`
Armazena os pesos dos modelos treinados.

- `yolov8/`: Pesos do YOLO (ex: `best.pt`, `last.pt`).
- `cnn/`: Pesos da CNN (ex: `cnn_model.pt` ou `.h5`).

### `scripts/`
Scripts principais que executam cada etapa do pipeline.

- `train_yolo.py`: Treina o YOLOv8 com base nas anotações.
- `crop_grains.py`: Usa o modelo YOLO para recortar os grãos das imagens.
- `train_cnn.py`: Treina uma CNN com os recortes organizados por classe.

### `utils/`
Funções reutilizáveis de apoio.

- `pre_processamento.py`: Funções para normalização, redimensionamento etc.
- `visualizacao.py`: Funções para plotar resultados e métricas.

### Arquivos principais

- `.gitignore`: Arquivos e pastas a serem ignorados pelo Git (ex: `.venv/`, `__pycache__/`, `models/`).
- `requirements.txt`: Lista de bibliotecas necessárias para rodar o projeto.
- `README.md`: Este documento com instruções e informações do projeto.
- `main.py`: Código principal que roda o sistema com webcam em tempo real.

---

## 🚀 Como usar

### 1. Instalar dependências

pip install -r requirements.txt

### 2. Treinar YOLOv8
Certifique-se de ter suas imagens anotadas no formato YOLO com um arquivo data.yaml configurado corretamente:

path: data/yolov8
train: images/train
val: images/val

### 3. Recortar grãos detectados
Após treinar o YOLO, use o modelo para detectar grãos e recortá-los:

python scripts/crop_grains.py
As imagens serão salvas em data/crops/, e depois você poderá movê-las manualmente para data/cnn/{classe}.

### 4. Treinar a CNN
Com os dados já organizados por torra:

python scripts/train_cnn.py

### 5. Rodar o sistema final com webcam

python main.py

🧠 Tecnologias utilizadas
YOLOv8 (Ultralytics) 
PyTorch (CNN) 
OpenCV (captura e visualização) 
Albumentations / torchvision (pré-processamento) 
Python 3.10 

---

### Artigos utilizados para ajudar na programação do software
* Applying Artificial Intelligence to Classify the Maturity Level of Coffee Beans During Roasting | https://www.researchgate.net/publication/374012737_Applying_Artificial_Intelligence_to_Classify_the_Maturity_Level_of_Coffee_Beans_During_Roasting
