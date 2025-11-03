
# 🐾 Project Pagu – Cat Detector

**Project Pagu** é um pipeline de processamento e estilização de vídeos com detecção automática de gatos.  
Criado para demonstrar como modelos de visão computacional podem ser aplicados em vídeos do mundo real, o projeto combina **processamento em chunks**, **detecção com YOLOv8**, e **estilização automática** dos frames.

---

## 🧠 O que é o Project Pagu?

O **Project Pagu** processa vídeos de entrada, dividindo-os em pequenos trechos (“chunks”) para facilitar o uso de GPU/CPU e manter o desempenho.  
Cada trecho é então analisado com um modelo **YOLOv8 (Ultralytics)**, capaz de detectar **gatos** (e outros objetos, se desejado).  
Após a detecção, o vídeo pode ser **estilizado** — aplicando transformações visuais (como filtros artísticos) apenas nas partes relevantes.

---

## ⚙️ Tecnologias Utilizadas

| Componente | Função |
|-------------|---------|
| **Google Colab** | Ambiente de execução acessível e gratuito com suporte a GPU |
| **Python 3.10+** | Linguagem base do pipeline |
| **Ultralytics YOLOv8** | Modelo de detecção de objetos (foco em gatos) |
| **OpenCV (cv2)** | Manipulação de frames de vídeo |
| **MoviePy** | Divisão, concatenação e exportação de vídeos |
| **NumPy** | Operações matriciais e numéricas |
| **tqdm** | Barra de progresso amigável durante o processamento |

---

## 🧩 Estrutura Técnica do Pipeline

1. **Entrada do Usuário**  
   O usuário define a pasta onde os vídeos de entrada estão localizados (`input_path`) e a pasta de saída (`output_path`).

2. **Processamento em Chunks**  
   Cada vídeo é dividido em blocos de duração configurável (`chunk_duration`, em segundos), o que evita travamentos em vídeos longos e permite processar partes menores de forma paralela.

3. **Detecção com YOLOv8**  
   Cada chunk é processado por um modelo YOLOv8, que detecta gatos e outros objetos.  
   As detecções podem ser visualizadas com bounding boxes diretamente sobre o vídeo.

4. **Estilização Opcional**  
   Frames detectados podem ser estilizados (por exemplo, transformados com efeitos artísticos) e salvos em uma nova pasta de saída.

5. **Concatenação Final**  
   Os chunks processados são reunidos novamente, gerando um vídeo final completo.

---

## 💻 Como Usar no Google Colab

### Passo 1️⃣ — Abrir no Colab
- Acesse o notebook diretamente pelo link do GitHub (por exemplo):  
  👉 [Abrir no Google Colab](https://colab.research.google.com/github/SEU_USUARIO/Project-Pagu/blob/main/stylize_cats_colab_cleaned_v2.ipynb)

---

### Passo 2️⃣ — Configurar o Ambiente
A primeira célula do notebook instala as dependências necessárias:
```python
!pip install -q ultralytics opencv-python-headless numpy moviepy tqdm
```
Execute-a (Ctrl+Enter).

Se estiver usando o **Google Drive**, o Colab pedirá autorização para montá-lo automaticamente.

---

### Passo 3️⃣ — Definir Caminhos e Parâmetros

Edite **somente** a célula de configuração.  
Ela contém instruções simples em português:

```python
# === CONFIGURAÇÃO DO USUÁRIO ===
input_path = "/content/drive/MyDrive/colab_inputs/cats"    # Pasta com vídeos originais
output_path = "/content/drive/MyDrive/colab_outputs/cats_chunks"  # Pasta de saída
chunk_duration = 8   # Duração de cada trecho (em segundos)
use_gpu = True       # Se GPU estiver disponível, define como True
```

> 💡 **Dica:** Use caminhos dentro do seu Google Drive para salvar os resultados.

---

### Passo 4️⃣ — Executar o Pipeline

Basta rodar as células seguintes na ordem.  
O pipeline faz automaticamente:

- A divisão dos vídeos em chunks  
- O processamento e detecção  
- A estilização (se configurada)  
- A concatenação final dos vídeos processados  

No final, o vídeo resultante estará na pasta de saída (`output_path`).

---

### Passo 5️⃣ — Verificar Resultados

Na pasta de saída você encontrará:
```
📂 cats_chunks/         # Chunks divididos do vídeo original
📂 cats_stylized/       # Vídeos com efeito de estilização
📄 log_execution.txt     # Log detalhado do processo
🎞️ final_output.mp4     # Resultado final (vídeo reconstruído)
```

---

## 🧪 Exemplo de Uso

1. Faça upload de um vídeo chamado `my_cat.mp4` para seu Drive em:
   ```
   /MyDrive/colab_inputs/cats/my_cat.mp4
   ```
2. No notebook, defina:
   ```python
   input_path = "/content/drive/MyDrive/colab_inputs/cats"
   output_path = "/content/drive/MyDrive/colab_outputs/cats_chunks"
   ```
3. Execute todas as células.
4. O resultado final será salvo em:
   ```
   /MyDrive/colab_outputs/cats_stylized/final_output.mp4
   ```

---

## 🧰 Estrutura do Repositório

```
Project-Pagu/
│
├── stylize_cats_colab_cleaned_v2.ipynb   # Notebook principal (executar no Colab)
├── README.md                             # Este arquivo
└── requirements.txt                      # Dependências (para execução local)
```

---

## 🐈‍⬛ Créditos e Licença

Desenvolvido por **Matheus Henrique**.  
Inspirado em aplicações de *Computer Vision* e *Generative AI*.  

Distribuído sob licença **MIT**, permitindo modificação e uso livre, desde que mantidos os créditos.

---

## 🌐 Contato e Contribuições

Contribuições são bem-vindas!  
Abra uma *issue* ou *pull request* no repositório.

---

### 🧡 “Pagu” — em homenagem à coragem criativa.
> “Ser independente é ser dona de si mesma, e isso é mais do que liberdade: é criação.”  
> — Patrícia Galvão (Pagu)
