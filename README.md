# 🏦 ETL Santander - Gerador de Mensagens de Marketing Personalizadas

Pipeline ETL desenvolvido como projeto do curso **"Explorando IA Generativa em um Pipeline de ETL com Python"** da DIO (Digital Innovation One) em parceria com o Santander. O projeto extrai dados de clientes, transforma utilizando IA generativa (Groq API) para criar mensagens de marketing personalizadas, e carrega os resultados em formato JSON estruturado.

## 📋 Descrição

Este projeto implementa um pipeline ETL (Extract, Transform, Load) completo que:
- **Extrai** dados de clientes a partir de um arquivo CSV
- **Transforma** os dados gerando mensagens de marketing personalizadas usando o modelo de IA Llama 3 através da API Groq
- **Carrega** os resultados enriquecidos em um arquivo JSON estruturado

O objetivo é demonstrar a aplicação prática de ETL combinado com inteligência artificial para criar conteúdo personalizado em escala, simulando um caso de uso real do setor bancário.

## 🚀 Tecnologias Utilizadas

- **Python 3.x**
- **Pandas** - Manipulação e análise de dados
- **Groq API** - Acesso ao modelo de IA Llama 3 (openai/gpt-oss-120b)
- **Jupyter Notebook** - Ambiente de desenvolvimento interativo
- **JSON** - Formato de saída estruturado

## 📁 Estrutura do Projeto

```
ETL-Santander/
│
├── Notebook/
│   └── ETL_DIO.ipynb          # Notebook principal com o pipeline ETL
│
├── Arquivos gerados/
│   ├── Data.csv               # Dados de entrada (usuários)
│   └── final_marketing_data.json  # Resultado final com mensagens personalizadas
│
└── README.md                  # Este arquivo
```

## 🔄 Pipeline ETL

### 1️⃣ Extract (Extração)
- Leitura de arquivo CSV contendo `UserID` e `Name` dos clientes
- Conversão dos dados para estrutura de dicionário Python
- Preparação da estrutura `news` para cada usuário

**Entrada:**
```csv
UserID,Name
1,Alice Silva
2,Bruno Souza
3,Carla Dias
4,Diego Ramos
5,Elena Luz
```

### 2️⃣ Transform (Transformação)
- Integração com a API Groq para geração de conteúdo
- Utilização do modelo `openai/gpt-oss-120b` (Llama 3)
- Geração de mensagens personalizadas de marketing bancário
- Cada mensagem é criada especificamente para o nome do cliente
- Limitação de 100 caracteres por mensagem para garantir concisão

**Prompt do Sistema:**
> "Você é um especialista em marketing bancário. Seja direto e cativante."

### 3️⃣ Load (Carga)
- Consolidação dos dados enriquecidos
- Exportação para arquivo JSON com encoding UTF-8
- Estrutura final inclui: UserID, Name e array de news com mensagens personalizadas

**Saída:**
```json
[
  {
    "UserID": 1,
    "Name": "Alice Silva",
    "news": [
      {
        "icon": "",
        "description": "Alice, investir hoje é plantar segurança para o amanhã."
      }
    ]
  }
]
```

## ⚙️ Como Executar

### Pré-requisitos

1. Python 3.7 ou superior instalado
2. Conta na plataforma Groq para obter API Key
3. Jupyter Notebook ou Google Colab

### Instalação

1. Clone este repositório:
```bash
git clone https://github.com/OYanEnrique/ETL-Santander.git
cd ETL-Santander
```

2. Instale as dependências:
```bash
pip install groq pandas
```

3. Configure sua chave da API Groq:
   - No Google Colab: Adicione a chave `GROQ_API_KEY` nos secrets
   - Localmente: Configure a variável de ambiente `GROQ_API_KEY`

### Execução

1. Abra o notebook:
```bash
jupyter notebook Notebook/ETL_DIO.ipynb
```

2. Execute as células sequencialmente:
   - Instalação das dependências
   - Criação do DataFrame de entrada
   - Extract: Leitura dos dados
   - Transform: Geração das mensagens com IA
   - Load: Salvamento do resultado final

## 📊 Resultados

O pipeline processa com sucesso os dados de entrada e gera mensagens de marketing personalizadas para cada cliente. Exemplos de saída:

- **Alice Silva**: "Alice, investir hoje é plantar segurança para o amanhã."
- **Bruno Souza**: "Bruno, invista hoje e faça seu futuro render mais."
- **Carla Dias**: "Carla, invista hoje e faça seu futuro render mais!"

## 🎯 Casos de Uso

Este projeto demonstra aplicações práticas como:
- Campanhas de marketing personalizadas em massa
- Comunicação bancária automatizada
- Engajamento de clientes através de mensagens contextualizadas
- Integração de IA generativa em processos de negócio

## 🔐 Segurança

- A API Key do Groq nunca é exposta no código
- Utilização de variáveis de ambiente para credenciais
- Dados de clientes são processados localmente

## 📝 Licença

Este projeto foi desenvolvido como parte do curso **"Explorando IA Generativa em um Pipeline de ETL com Python"** da DIO em parceria com o Santander.

## 👨‍💻 Autor

Desenvolvido por Yan Enrique como projeto do curso **"Explorando IA Generativa em um Pipeline de ETL com Python"** da Digital Innovation One (DIO) - Santander Bootcamp.

## 🙏 Agradecimentos

- [Digital Innovation One (DIO)](https://www.dio.me/)
- Santander
- Groq AI pela disponibilização da API

---

⭐ Se este projeto foi útil para você, considere dar uma estrela no repositório!
