# 📊 Análise Estatística de Navegação e Comportamento de Compra em E-commerce

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?style=for-the-badge&logo=python&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-2.3.2-013243?style=for-the-badge&logo=numpy&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-Data%20Viz-3776AB?style=for-the-badge)

Este projeto realiza uma **Análise Estatística Descritiva e Exploratória** utilizando vetores e matrizes otimizadas com **NumPy** para entender o comportamento de navegação de usuários em uma plataforma de e-commerce. 

O objetivo principal é substituir decisões baseadas em intuição por estratégias orientadas a dados (*Data-Driven Marketing*), identificando padrões que diferenciam **clientes de alto valor** de visitantes casuais e mapeando quais comportamentos mais impactam a receita final.

---

## 📌 Sumário

- [Contexto e Problema de Negócio](#-contexto-e-problema-de-negócio)
- [Perguntas-Chave de Negócio](#-perguntas-chave-de-negócio)
- [Tecnologias Utilizadas](#-tecnologias-utilizadas)
- [Metodologia e Geração de Dados](#-metodologia-e-geração-de-dados)
- [Principais Insights e Resultados](#-principais-insights-e-resultados)
- [Recomendações Práticas de Negócio](#-recomendações-práticas-de-negócio)
- [Como Executar o Projeto](#-como-executar-o-projeto)

---

## 🎯 Contexto e Problema de Negócio

### Contexto
A plataforma de e-commerce monitora diversas métricas de interação, como número de visitas, tempo de permanência no site, adição de itens ao carrinho e valor total gasto. Contudo, esses dados estavam sendo subutilizados, resultando em métricas superficiais e ações de marketing genéricas.

### Problema
- **Marketing Genérico:** Campanhas "tamanho único" que geram baixo engajamento e desperdício de orçamento.
- **Perda de Oportunidades:** Incapacidade de engajar proativamente clientes com alto potencial de compra ou converter visitantes interessados.
- **Decisões Sem Embasamento:** Falta de clareza quantitativa sobre quais comportamentos de navegação realmente impulsionam o faturamento.

---

## ❓ Perguntas-Chave de Negócio

1. **Qual é o perfil médio do usuário** em termos de visitas, tempo de navegação e valor de compra (ticket médio)?
2. **Quais são os comportamentos distintos dos clientes de "Alto Valor"?** Eles visitam mais o site ou passam mais tempo navegando?
3. **Qual é o comportamento dos visitantes que não realizam compras?** Onde reside a oportunidade de conversão?
4. **Existe correlação estatisticamente relevante** entre o tempo gasto no site, a quantidade de itens no carrinho e o valor final da compra?

---

## 🛠️ Tecnologias Utilizadas

- **Python 3.10+**: Linguagem base do projeto.
- **NumPy (v2.3.2)**: Processamento vetorial de alta performance para cálculos estatísticos (médias, medianas, desvio padrão, matrizes de correlação e indexação booleana).
- **Pandas**: Estruturação de dados para exibição tabulada e relatórios.
- **Matplotlib / Seaborn**: Construção de gráficos estatísticos (histogramas de distribuição e heatmap de correlação).
- **Watermark**: Versionamento dos pacotes e reprodutibilidade.

---

## 🧮 Metodologia e Geração de Dados

Para simular o ambiente real do e-commerce, foi gerada uma base fictícia contendo **500 usuários** com variáveis interdependentes via distribuições de probabilidade:

- `visitas`: Número de acessos mensais (distribuição discreta entre 1 e 50).
- `tempo_no_site`: Tempo total em minutos (distribuição normal $\mu=20, \sigma=5$, com ajuste proporcional às visitas).
- `itens_no_carrinho`: Quantidade de produtos adicionados (correlacionado ao tempo e visitas).
- `valor_compra`: Valor final em R$ (preço médio por item + variação aleatória, garantindo R$ 0 para quem não adicionou itens).

---

## 📈 Principais Insights e Resultados

### 1. Perfil Geral do Consumidor
* **Ticket Médio:** R$ 252,70
* **Mediana do Valor:** R$ 248,13 *(indica distribuição simétrica e consistente)*
* **Desvio Padrão:** R$ 106,94 *(alta variação, indicando presença de diferentes personas)*
* **Média de Visitas:** ~26 acessos/mês
* **Tempo Médio de Navegação:** ~33 minutos/sessão

### 2. Segmentação: Clientes de "Alto Valor" (Compras > R$ 250)
* Representam aproximadamente **49% da base (245 clientes)**.
* **Média de Visitas:** 33,29 acessos/mês (+28% vs. média geral).
* **Tempo no Site:** 37,11 minutos (+13% vs. média geral).
* **Insight:** Frequência de acesso e tempo de permanência possuem forte ligação com a conversão em compras de alto valor.

### 3. Matriz de Correlação
| Variável | Visitas | Tempo no Site | Itens no Carrinho | Valor da Compra |
| :--- | :---: | :---: | :---: | :---: |
| **Visitas** | 1.00 | 0.81 | 0.65 | **0.65** |
| **Tempo no Site** | 0.81 | 1.00 | 0.60 | **0.59** |
| **Itens no Carrinho**| 0.65 | 0.60 | 1.00 | **1.00** |
| **Valor da Compra** | **0.65** | **0.59** | **1.00** | 1.00 |

> **Conclusão Estatística:** A quantidade de itens no carrinho possui correlação linear direta com o valor total da compra ($r = 1.00$). O tempo no site e o número de visitas apresentam correlação positiva moderada a forte ($r pprox 0.60$ a $0.65$), validando a hipótese de que estratégias que retêm o usuário na plataforma elevam o faturamento.

---

## 💡 Recomendações Práticas de Negócio

1. **Programa de Fidelidade para Clientes de Alto Valor:**
   - Criar ofertas exclusivas e acesso antecipado a lançamentos para os 245 clientes identificados no segmento de alto valor, visando maximizar o *Customer Lifetime Value* (LTV).

2. **Incentivo à Expansão do Carrinho (*Cross-Selling* / Combos):**
   - Como o número de itens é o fator determinante do faturamento, implementar sugestões de produtos complementares ("Leve Junto"), frete grátis acima de X itens e descontos progressivos.

3. **Estratégias de Retenção de Navegação (UX/Product):**
   - Desenvolver recomendações personalizadas na *home* e buscas otimizadas para manter o usuário engajado por mais tempo na plataforma, aproveitando a correlação positiva de $0.59$ com o ticket final.

---

## 📁 Estrutura do Repositório

```bash
├── data/                    # Dados gerados / exportados (se aplicável)
├── notebooks/
│   └── analise_estatistica_numpy.ipynb  # Notebook Jupyter principal
├── .gitignore               # Arquivos ignorados pelo Git
├── README.md                # Descrição geral do projeto
└── requirements.txt         # Bibliotecas e versões necessárias
```

---

## 🚀 Como Executar o Projeto

1. **Clone o repositório:**
   ```bash
   git clone https://github.com/seu-usuario/seu-repositorio.git
   cd seu-repositorio
   ```

2. **Crie um ambiente virtual (opcional, mas recomendado):**
   ```bash
   python -m venv venv
   source venv/bin/activate  # No Linux/Mac
   # ou
   .\venv\Scripts\activate   # No Windows
   ```

3. **Instale as dependências:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Execute o Jupyter Notebook:**
   ```bash
   jupyter notebook notebooks/analise_estatistica_numpy.ipynb
   ```
