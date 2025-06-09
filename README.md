# Desafio Técnico – DATA ENGINEER JR (Backend Python)

## 🎯 Objetivo

Avaliar a capacidade de manipular e explorar dados utilizando **Python** com **DuckDB**, além de construir uma pipeline simples de Machine Learning baseada em dados públicos.

## 📦 Dataset

Escolha um dataset do [Kaggle](https://www.kaggle.com/datasets) que seja simples e bem documentado.

> **Dica:** Prefira datasets com colunas categóricas, valores faltantes e tarefa de classificação binária.


## 📌 Etapas do Desafio

### 1. Ingestão e Armazenamento

* Baixe o dataset escolhido do Kaggle.
* Carregue os dados em uma instância local de **DuckDB**, via Python.

### 2. Exploração de Dados (EDA)

Utilize **consultas SQL no DuckDB** para responder:

* Quantas linhas e colunas o dataset possui?
* Existem valores nulos? Em quais colunas e quantos?
* Qual a correlação entre variáveis numéricas?

### 3. Pré-processamento

* Trate valores nulos adequadamente.
* Converta variáveis categóricas para numéricas (One-Hot Encoding ou Ordinal).
* Normalize ou padronize colunas numéricas, se necessário.

### 4. Modelagem

* Faça a divisão entre treino e teste com `train_test_split`.
* Avalie utilizando: **accuracy**, **precision**, **recall** e **F1-score**.

### 5. Apresentação
Você precisará nos apresentar o seu projeto em uma videoconferência de até 15 minutos.
Durante essa apresentação, avaliaremos não apenas as decisões técnicas tomadas, mas também sua:

Capacidade de comunicação
Clareza na explicação
Organização do raciocínio
Comportamento colaborativo e alinhamento com trabalho em equipe

Além do domínio técnico, buscamos alguém que saiba se comunicar bem com diferentes áreas e lidar com os desafios naturais de alinhamento e compartilhamento de informações em ambientes multidisciplinares.


### ## ⏰ Prazo de Entrega

*\*3 dias corridos\*\* após o envio deste desafio. Caso termina antes, ficamos disponíveis para falar ok? 

Boa sorte! 🍀


# Explicações de decisões técnicas:


## Decisões de Código:

* A Utilização de variáveis de ambiente KAGGLE_USERNAME e KAGGLE_KEY foi uma decisão técnica adotada como boa prática de segurança para evitar o vazamento das chaves no repositório.

* Utilização de biblioteca DuckDB ao invés de pandas como forma de melhorar a performance das consultas ao banco de dados.

* Utilização de funções como execute_query (que executa qualquer query SQL) para evitar repetições de código.

* Utilização de DocStrings e tipagem de argumentos em funções para melhorar a documentação do código.

## Decisões de Machine Learning:

* Remoção das features PassangerId, Name e Ticket pois não possuem poder preditivo considerando a definição do dicionário de dados.

* Valores nulos em Age foram tratados com a média da PClass em que o passageiro pertencia pois as médias de idade em cada classe eram bem diferentes.

* Coluna Cabin removido pois apresentava 77% de dados nulos. O tratamento desses dados poderia resultar em uma distribuição muito distorcida de realidade e assim levar o modelo à conclusões erradas.

* Os valores nulos em Embarked são dados faltantes e por isso somente as linhas com dados nulos nessa feature foram removidas.

* Utilização de correlações estatísticas para verificar se há relações lineares.

* Uma feature (PClass) possuia correlação próxima de forte e por isso realizei experimento com regressão logística.


# Instruções de uso:
Siga abaixo o passo a passo para rodar o arquivo Notebook.ipynb no VSCode:

1. Abra uma pasta onde deseja clonar o repositório.

2. Abra o terminal dentro dessa pasta e executar o seguinte código: git clone https://github.com/lcfjunior00/desafio-gdia-backend.git

3. Crie um ambiente virtual na pasta principal do projeto e depois ative-o e baixe as bibliotecas que estão em requirements.txt 

4. Gere chave API no kaggle:

4.1. Vá até o site kaggle.com e acesse seu perfil.

4.2. No canto superior direito, clique na bolinha com a foto do seu perfil.

4.3. Clique em settings.

4.4. Menu API, clica em "Create New Token".

4.5. Será baixado um arquivo chamado kaggle.json

5. Pegue as informações de username e key no arquivo kaggle.json e preencha o arquivo .env.example. Em seguida, renomeie o arquivo para .env

5.1. É importante lembrar que o arquivo .venv não deve ser versionado. (confira se o arquivo .venv está em .gitignore)

6. Certifique-se de ter instalado na sua máquina a extensão Jupyter para o VSCode.

7. Em seguida, execute o arquivo Notebook.ipynb