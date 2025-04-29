# 🏡 Predição de Preços de Imóveis - Airbnb Rio de Janeiro

![Python](https://img.shields.io/badge/Python-3.11.7-blue.svg)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)
![Data Science](https://img.shields.io/badge/Data-Science-green.svg)
![License](https://img.shields.io/badge/License-MIT-blue.svg)

## 📋 Sobre o Projeto

Este projeto tem como objetivo desenvolver um modelo de Machine Learning para prever o preço de aluguel de imóveis no Rio de Janeiro através da plataforma Airbnb. A solução foi construída para ajudar tanto proprietários quanto locatários:

- **Para proprietários**: Saber quanto cobrar pela diária do seu imóvel
- **Para locatários**: Avaliar se um imóvel está com preço atrativo em relação à média do mercado

O projeto utiliza técnicas avançadas de Ciência de Dados, desde a análise exploratória até a construção e avaliação de modelos, finalizando com o deploy de uma aplicação web interativa.

## 📊 Análise de Dados

### Dataset

- **Fonte**: [Airbnb Rio de Janeiro - Dataset no Kaggle](https://www.kaggle.com/datasets/allanbruno/airbnb-rio-de-janeiro)
- **Período**: Abril de 2018 a Maio de 2020 (exceto junho de 2018)
- **Moeda**: Reais (R$)
- **Tamanho Inicial**: Mais de 900.000 registros

### Tratamento de Dados

1. **Limpeza Inicial**:

   - Remoção de colunas com mais de 300.000 valores ausentes
   - Exclusão de linhas com valores nulos
   - Tratamento de valores monetários (remoção de '$' e ',')

2. **Seleção de Features**:

   - **Variáveis Numéricas**:
     - latitude, longitude
     - accommodates, bathrooms, bedrooms, beds
     - extra_people, minimum_nights
     - ano, mes, nr_amenities
     - host_listings_count
   - **Variáveis Booleanas**:
     - host_is_superhost
     - instant_bookable
   - **Variáveis Categóricas**:
     - property_type
     - room_type
     - bed_type
     - cancellation_policy

3. **Tratamento de Outliers**:

   - Aplicação da regra IQR (Q1 - 1.5*IQR, Q3 + 1.5*IQR)
   - Remoção de valores extremos em:
     - price
     - extra_people
     - host_listings_count
     - accommodates
     - bathrooms
     - bedrooms
     - beds
     - minimum_nights
     - nr_amenities

4. **Tratamento de Categorias**:
   - Agrupamento de categorias pouco frequentes em 'outros'
   - Aplicação de One-Hot Encoding para variáveis categóricas
   - Conversão de valores booleanos para 0/1

## 🤖 Modelagem

### Modelos Testados

1. **Random Forest Regressor**
2. **Linear Regression**
3. **Extra Trees Regressor**

### Métricas de Avaliação

- **R² (Coeficiente de Determinação)**
- **RMSE (Root Mean Square Error)**

### Resultados

- **Modelo Escolhido**: Extra Trees Regressor
  - R²: 97.51%
  - RMSE: 41.86

### Importância das Features

As features mais relevantes para o modelo foram:

1. latitude
2. longitude
3. accommodates
4. bedrooms
5. bathrooms
6. beds
7. nr_amenities
8. minimum_nights
9. extra_people
10. host_listings_count

## 🚀 Deploy

### Interface Web

Desenvolvida utilizando Streamlit, permite:

- Inserção de características do imóvel
- Visualização de previsão de preço em tempo real
- Análise de diferentes configurações
- Comparação de preços

### Arquivos Gerados

- `modelo.joblib`: Modelo treinado
- `dados.csv`: Base de dados processada
- `DeployProjetoAirbnb.py`: Aplicação web

## ⚙️ Tecnologias utilizadas

### Linguagens e Frameworks

- Python 3.11.7
- Jupyter Notebook
- Streamlit

### Bibliotecas de Data Science

- Pandas: Manipulação e análise de dados
- NumPy: Computação numérica
- Scikit-learn: Machine Learning
- Matplotlib/Seaborn: Visualização de dados
- Joblib: Serialização de modelos

## 🚀 Como executar o projeto

1. Clone este repositório:

```bash
git clone https://github.com/Rodrigogj8/airbnb-price-prediction-rio-ds.git
cd airbnb-price-prediction-rio-ds
```

2. Instale as dependências:

```bash
pip install -r requirements.txt
```

3. Baixe o dataset do [Kaggle](https://www.kaggle.com/datasets/allanbruno/airbnb-rio-de-janeiro)

4. Execute a aplicação web:

```bash
streamlit run app/DeployProjetoAirbnb.py
```

## 📈 Conclusões

- O modelo desenvolvido apresenta alta precisão (R² de 97.51%)
- A localização geográfica (latitude/longitude) é o fator mais importante na determinação do preço
- Características do imóvel (quartos, banheiros, camas) têm impacto significativo
- Amenidades e políticas de cancelamento também influenciam o preço
- O modelo é eficaz para imóveis comuns, excluindo outliers de alto padrão

## 👨‍💻 Autor

Rodrigo Gonçalves
