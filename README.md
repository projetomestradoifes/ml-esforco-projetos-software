# Avaliação de Algoritmos de Aprendizado de Máquina para Estimativa de Esforço em Projetos de Software a partir de Descrições Textuais de Requisitos

Este projeto faz parte de um trabalho de mestrado e tem como objetivo avaliar diferentes algoritmos de Aprendizado de Máquina (ML) — incluindo modelos clássicos e baseados em BERT — para estimar o esforço de tarefas de desenvolvimento de software (em pontos de história) a partir de descrições textuais de requisitos extraídas de sistemas como o Jira.

---

## 1. Visão Geral

O repositório contém scripts para:

- **Pré-processamento** de datasets contendo requisitos textuais e seus story points.
- **Treinamento e avaliação** de modelos de ML clássicos (ex.: Random Forest, XGBoost, SVR) e modelos baseados em **BERT**.
- Execução de experimentos **intra-dataset** e **inter-dataset**.
- Geração e exportação de resultados em formato CSV para análise posterior.

---

## 2. Estrutura de Pastas

```
├── datasets_all/                # Datasets originais (não versionados)
├── datasets_all_processados/    # Datasets processados prontos para treino/avaliação
├── folds/                       # Divisões para validação cruzada
├── preprocessing.py              # Script de pré-processamento
├── run_ml_experiments.py         # Execução dos modelos clássicos de ML
├── run_bert_experiments.py       # Execução dos modelos BERT
├── ml_evaluation.py              # Avaliação consolidada dos modelos clássicos
├── bert_evaluation.py            # Avaliação consolidada dos modelos BERT
├── utils.py                      # Funções auxiliares
└── requirements.txt              # Lista de dependências do projeto
```

> **Observação:** Os datasets originais não são versionados neste repositório. É necessário colocá-los manualmente na pasta `datasets_all/` antes de executar os scripts.

---

## 3. Configurações Importantes

Antes de executar, verifique e ajuste nos scripts:

- **Caminhos para pastas**:
```python
DIRETORIO_DATASET_BRUTO = 'caminho/para/datasets_all'
DIRETORIO_DATASET_PROCESSADO = 'caminho/para/datasets_all_processados'
```

- **Número de épocas de treinamento (BERT)**:
```python
EPOCHS = 5
```

- **Limite opcional de registros para experimentos rápidos**:
```python
LIMITAR_QUANTIDADE_REGISTROS = True
QUANTIDADE_REGISTROS_SE_LIMITADO = 15
```

---

## 4. Instalação

**Requisitos:**
- Python 3.8+
- Git

**Passos:**

1. Clone este repositório:
```bash
git clone https://github.com/projetomestradoifes/ml-esforco-projetos-software.git
cd ml-esforco-projetos-software
```

2. Crie e ative um ambiente virtual:
```bash
python -m venv venv

# Windows
venv\Scripts\activate
```

3. Instale as dependências:
```bash
pip install -r requirements.txt
```

---

## 5. Execução

### 5.1 Pré-processamento
Prepara os datasets para uso nos modelos.
```bash
python preprocessing.py
```

### 5.2 Treinamento de modelos clássicos de ML
Executa todos os modelos definidos e gera resultados em CSV.
```bash
python run_ml_experiments.py
```

### 5.3 Treinamento de modelos BERT
Executa o pipeline de fine-tuning do BERT.
```bash
python run_bert_experiments.py
```

### 5.4 Avaliação dos modelos
```bash
# Modelos clássicos
python ml_evaluation.py

# Modelos BERT
python bert_evaluation.py
```

---

## 6. Resultados

Após a execução, os resultados serão gerados em:
- `resultados_modelos.csv` — métricas de desempenho (MAE, RMSE, R², etc.).
- Pastas dentro de `folds/` — dados de cada divisão para validação cruzada.

---

## 7. Citação

Se este projeto for útil para sua pesquisa, por favor cite:

```bibtex
@inproceedings{sobrenome2025esforco,
  title={Avaliação de Algoritmos de Aprendizado de Máquina para Estimativa de Esforço em Projetos de Software a partir de Descrições Textuais de Requisitos},
  author={Seu Nome Completo},
  booktitle={Nome do Evento ou Periódico},
  year={2025}
}
```

---

## 8. Licença

Este projeto está licenciado sob a licença MIT - veja o arquivo [LICENSE](LICENSE) para mais detalhes.
