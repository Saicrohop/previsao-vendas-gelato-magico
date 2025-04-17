# Previsão de Vendas de Sorvete (Gelato Mágico) com Azure AutoML

Este documento resume os passos realizados no Azure Machine Learning para criar um modelo de previsão de vendas de sorvete usando AutoML.

---

## 1. Configuração do Ambiente Azure ML

### **Passo 1: Criação do Workspace Azure ML**
**Ação:** Criação de um novo Workspace no Azure Machine Learning.

**Detalhes Principais:**
- **Assinatura:** Rendervm
- **Grupo de Recursos:** DL-100
- **Nome do Workspace:** workspaceido
- **Região:** East US
- **Recursos Associados:** Criação automática de Storage Account, Key Vault e Application Insights vinculados ao workspace.

---

### **Passo 2: Confirmação da Implantação**
**Ação:** Verificação da conclusão bem-sucedida da implantação do Workspace e seus recursos associados.

---

### **Passo 3: Acesso aos Notebooks**
**Ação:** Navegação até a seção "Notebooks" dentro do Workspace `workspaceido` para gerenciar arquivos e iniciar o desenvolvimento.

---

### **Passo 4: Criação da Instância de Computação (Compute Instance)**
**Ação:** Criação de uma máquina virtual para execução interativa de notebooks.

**Detalhes:**
- **Nome:** italotorres081
- **Tipo:** CPU
- **Tamanho:** Standard_E4ds_v4 (4 núcleos, 32 GB RAM)

---

### **Passo 5: Criação do Cluster de Cálculo (Compute Cluster)**
**Ação:** Criação de um cluster gerenciado para treinamento de modelos, com escalabilidade automática.

**Detalhes:**
- **Tipo de VM:** Standard_DS3_v2 (Uso geral)
- **Nós:** Mínimo 0, Máximo 1
- **Tempo de Ociosidade antes de desligar:** 120 segundos

---

## 2. Preparação e Execução do AutoML

### **Passo 6: Criação do Ativo de Dados (Data Asset)**
**Ação:** Registro do conjunto de dados no Azure ML para ser utilizado nos experimentos.

**Detalhes:**
- **Nome:** sorvetes (ou o nome definido)
- **Tipo:** Tabular (adequado para dados como CSV)

---

### **Passo 7: Submissão do Trabalho AutoML**
**Ação:** Início de um novo trabalho de Machine Learning Automatizado.

**Detalhes:**
- **Nome do Experimento:** experimento-automl (novo)
- **Nome do Trabalho:** (Gerado automaticamente ou definido, ex: `automl_previsao_vendas`)

---

### **Passo 8: Configuração da Tarefa AutoML**
**Ação:** Definição dos parâmetros para a execução do AutoML.

**Detalhes:**
- **Tipo de Tarefa:** Regressão
- **Conjunto de Dados:** sorvetes
- **Coluna de Destino (Target):** Columna3
- **Limite de Tempo:** 15 minutos
- **Validação:** Automática

---

## 3. Resultados e Avaliação

### **Passo 9: Modelos Gerados pelo AutoML**
**Ação:** Análise dos modelos treinados e classificados pelo AutoML com base na métrica primária (RMSE Normalizado para Regressão).

**Resultado Principal:** O modelo **VotingEnsemble** foi identificado como o melhor, apresentando o menor erro.

---

### **Passo 10: Métricas de Avaliação do Melhor Modelo**
**Ação:** Análise detalhada das métricas de desempenho do modelo **VotingEnsemble**.

**Métricas Principais:**
- **Erro Absoluto Médio (MAE):** 12.183
- **Erro Quadrático Médio Normalizado (RMSE Normalizado):** 0.15879
- **Pontuação R²:** 0.29949
- **Correlação de Spearman:** 0.67214

---

## Conclusão

O processo demonstrou a configuração do ambiente no Azure ML e a execução de um experimento AutoML para prever vendas de sorvete. O modelo **VotingEnsemble** foi o melhor encontrado automaticamente, com as métricas de avaliação indicando seu desempenho (R² de aproximadamente 0.30). Este modelo pode ser considerado para implantação ou refinamento adicional.
