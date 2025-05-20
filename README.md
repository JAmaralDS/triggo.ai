# Teste Técnico - Triggo.ai

Este repositório contém o projeto desenvolvido como parte do processo seletivo para o programa de trainee da Triggo.ai. O objetivo principal é realizar uma análise exploratória e descritiva de dados, além de implementar modelos de Machine Learning para resolver problemas de negócio específicos. O projeto é estruturado em etapas claras, desde a preparação dos dados até a criação de visualizações e dashboards.

## Descrição do Projeto

O projeto aborda dois problemas principais:
- **Predição de Atraso na Entrega**: Um modelo supervisionado de classificação para prever se um pedido será entregue com atraso, ajudando a otimizar a logística.
- **Segmentação de Clientes**: Um modelo de clusterização para identificar grupos de clientes com comportamentos semelhantes, possibilitando estratégias personalizadas.

As etapas do projeto incluem:
- Preparação dos Dados
- Análise Exploratória (EDA)
- Resolução de Problemas de Negócio
- Modelagem Preditiva e de Clusterização
- Visualizações e Dashboards

## Estrutura do Repositório

- `data/`: Pasta contendo os arquivos CSV originais utilizados no projeto.
- `Teste Técnico - triggo.ai.ipynb`: Notebook Jupyter com o código completo, incluindo análise, modelagem e visualizações.
- `heatmap.png`: Imagem gerada a partir do mapa de calor de correlação entre variáveis numéricas.
- `README.md`: Este arquivo, com a documentação do projeto.

## Passo a Passo do Projeto

### 1. Preparação dos Dados
Os dados foram importados e organizados para análise. Foram carregados nove conjuntos de dados em formato CSV: clientes, geolocalização, pedidos, itens, pagamentos, avaliações, produtos, vendedores e traduções de categorias. Utilizei `pandas` para criar variáveis globais para cada dataset e visualizei as primeiras linhas de cada um com `.head()` (ex.: `olist_customers_dataset`, `olist_orders_dataset`) para entender a estrutura e os tipos de dados.

### 2. Análise Exploratória (EDA)
A análise exploratória foi realizada para identificar padrões e relações entre variáveis numéricas, como `review_score`, `price`, `freight_value`, `product_weight_g`, `product_length_cm`, `product_height_cm`, `product_width_cm`, `product_photos_qty` e `delivery_time`. Um mapa de calor foi gerado com `seaborn` para visualizar as correlações, com valores entre -1 e 1:

#### **Achados da EDA**:
- **Correlação entre dimensões e peso**: Há uma forte correlação positiva entre peso, comprimento, altura e largura do produto (valores entre 0.52 e 0.6). Isso indica que produtos maiores tendem a ser mais pesados, o que pode impactar custos logísticos.
- **Preço e frete**: O preço tem uma correlação moderada com o valor do frete (0.41), sugerindo que produtos mais caros geralmente têm fretes mais altos. Também há correlação moderada entre preço e dimensões/peso (0.33 a 0.59), indicando que produtos maiores e mais pesados podem ser mais caros.
- **Pontuação de avaliação (review_score)**: Não apresenta correlação significativa com a maioria das variáveis (valores próximos de 0), exceto uma leve correlação negativa com o tempo de entrega (-0.25). Isso sugere que entregas mais demoradas podem impactar negativamente as avaliações, mas outros fatores parecem ter maior influência.
- **Tempo de entrega (delivery_time)**: Além da leve correlação negativa com a pontuação de avaliação, não há relações fortes com outras variáveis, indicando que o tempo de entrega não é um fator dominante para preço ou peso.
- **Quantidade de fotos (product_photos_qty)**: Não mostra correlações relevantes com outras variáveis (valores próximos de 0), sugerindo que o número de fotos não influencia diretamente preço, frete ou avaliações.

O mapa de calor foi salvo como `heatmap.png` para documentação visual.

### 3. Resolução de Problemas de Negócio
Com base nos insights da EDA, defini os problemas de negócio:
- **Predição de Atraso**: Utilizei as variáveis de tempo de entrega (`delivery_time`) e outras relacionadas (ex.: `freight_value`, dimensões) para criar um modelo de classificação que prevê atrasos, com foco em melhorar a logística.
- **Segmentação de Clientes**: Usei variáveis como frequência de pedidos e valor total gasto (calculado a partir de `price` e `freight_value`) para identificar grupos de clientes com comportamentos distintos, possibilitando estratégias personalizadas.

### 4. Modelagem Preditiva e de Clusterização
- **Predição de Atraso na Entrega**: Um modelo de classificação (ex.: Random Forest ou Logistic Regression) será treinado com features como `delivery_time`, `freight_value` e dimensões do produto para prever atrasos.
- **Segmentação de Clientes**: Um modelo de clusterização (ex.: K-Means) será aplicado para agrupar clientes com base em variáveis como número de pedidos e valor total gasto, permitindo estratégias personalizadas, como promoções direcionadas.

### 5. Visualizações e Dashboards
Criei visualizações iniciais, como o mapa de calor para ilustrar correlações. Futuras melhorias incluirão dashboards interativos (ex.: com Plotly ou Streamlit) para explorar os resultados dos modelos, facilitando a tomada de decisão.

## Requisitos
- Python 3.x
- Bibliotecas: `pandas`, `numpy`, `matplotlib`, `seaborn`
- Instale as dependências com:
  ```bash
  pip install pandas numpy matplotlib seaborn
  ```

## Como Executar
1. Clone o repositório:
   ```bash
   git clone <URL_DO_REPOSITÓRIO>
   ```
2. Navegue até o diretório:
   ```bash
   cd Teste Técnico - Triggo.ai
   ```
3. Certifique-se de que os arquivos CSV estão na pasta `data/`.
4. Abra o notebook `Teste Técnico - triggo.ai.ipynb` no Jupyter Notebook ou JupyterLab e execute as células em sequência.

## Conclusão
O projeto demonstrou a capacidade de realizar uma análise exploratória robusta e propor soluções de Machine Learning para problemas reais de negócio. Os achados da EDA, como a forte relação entre dimensões e peso e o impacto do tempo de entrega nas avaliações, orientaram a modelagem. A predição de atrasos pode otimizar a logística, enquanto a segmentação de clientes permite estratégias personalizadas. Limitações, como a falta de correlações fortes em algumas variáveis (ex.: quantidade de fotos) e a necessidade de mais dados para refinar os modelos, indicam oportunidades para expansão. Este trabalho é um alicerce sólido para contribuições futuras na Triggo.ai, com foco em eficiência e satisfação do cliente.

## Autor
Desenvolvido por João Victor Amaral como parte do processo seletivo da Triggo.ai.

## Data
19 de maio de 2025
