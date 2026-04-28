# proj2-CompVisual

# Projeto de Visão Computacional: Detecção de Bordas

**Felipe Carvalho** - RA: 10409804
**Gabriel Rodrigues** - RA: 10409071
**Giulia Araki** - RA: 10408954


Este projeto em Python, desenvolvido inicialmente no Jupyter Notebook/Google Colab, aplica diferentes algoritmos de detecção de bordas em uma imagem e compara os resultados obtidos. O algoritmo de **Canny** é utilizado como referência matemática e visual (baseline) para avaliar o desempenho dos filtros de **Sobel** e **Prewitt**.

##  Funcionalidades

- **Pré-processamento:** Carregamento da imagem fornecida pelo usuário, conversão para escala de cinza e aplicação de desfoque (*Gaussian Blur*) para redução de ruído.
- **Detecção de Bordas:**
  - **Método de Canny** (Baseline)
  - **Filtro de Sobel**
  - **Filtro de Prewitt**
- **Análise e Métricas:** Comparação rigorosa dos filtros Sobel e Prewitt com a saída de Canny calculando as seguintes métricas:
  - Classificações de Verdadeiros Positivos (TP), Falsos Positivos (FP) e Falsos Negativos (FN)
  - Precisão (Precision), Recall e F1-Score
  - Interseção sobre União (IoU)
  - Diferença percentual de pixels
- **Visualização de Dados:**
  - Painel agregador com as imagens originais e as tratadas por cada filtro.
  - Diferença colorida destacando acertos e erros (Verde = Acerto, Vermelho/Azul = Falsos Positivos/Negativos).
  - Mapas de calor (Heatmaps) das diferenças absolutas.
  - Gráficos de barras comparando visualmente as métricas e a diferença percentual.

##  Tecnologias Utilizadas

- [Python 3](https://www.python.org/)
- [OpenCV](https://opencv.org/) (`cv2`) - Processamento central de imagens
- [NumPy](https://numpy.org/) - Operações matemáticas e matriciais
- [Matplotlib](https://matplotlib.org/) - Geração analítica dos gráficos e heatmaps
- [Google Colab](https://colab.research.google.com/) - Ambiente base de execução (uso integrado com pacotes como `google.colab.patches`)

##  Como Executar

1. Abra o arquivo `ProjetoCompVis.ipynb` no Google Colab.
2. Certifique-se de executar a primeira célula para instalar as dependências obrigatórias (ex: `!pip install opencv-python`).
3. Execute a célula de upload (`files.upload()`) e insira a imagem que deseja analisar (por exemplo, `raiox.jpeg`).
4. Execute o bloco de código principal. O script irá automaticamente:
   - Limpar e recriar o diretório local `output/`.
   - Executar os filtros de imagem.
   - Apresentar o painel visual de resultados.
   - Imprimir as tabelas de métricas e o veredito final indicando qual filtro (Sobel ou Prewitt) performou de forma mais semelhante ao Canny.

##  Estrutura de Saída (Pasta `output/`)

Ao final da execução, uma pasta `/output/` será gerada no ambiente e contará com os seguintes resultados:

- `gray.png`: Imagem no formato escala de cinza.
- `canny.png`, `sobel.png`, `prewitt.png`: Máscaras das bordas detectadas isoladamente.
- `diff_sobel_color.png` e `diff_prewitt_color.png`: Mapeamentos visuais e coloridos de correspondência contra o baseline do Canny.
- `painel.png`: Um agrupamento resumido para comparação lado a lado.
- `heatmap_sobel.png` / `heatmap_prewitt.png`: Mapas de calor representando as áreas de variação.
- `grafico_metricas.png` e `grafico_diferenca.png`: Representações estatísticas dos resultados obtidos.

## 📊 Veredito de Avaliação

Ao fim da rotina, um score médio unindo o **F1-Score** e a métrica **IoU** é calculado. O filtro que apresentar a maior pontuação combinada ganha o "Veredito", demonstrando ser matematicamente a técnica de aproximação mais eficaz ao Canny para aquela imagem.
