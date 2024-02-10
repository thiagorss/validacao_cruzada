# Título do Projeto

Este é um projeto de aprendizado de máquina com o objetivo de fornecer uma estrutura flexível para realizar experimentos de classificação utilizando métodos do `scikit-learn` e otimização de hiperparâmetros com o `Optuna`.

## Estrutura do Código

O projeto consiste em três partes principais:

### 1. Experimento

A classe `Experimento` permite a execução de experimentos de aprendizado de máquina. Ela recebe folds de dados, um método de aprendizado de máquina e opcionalmente uma classe para otimização de hiperparâmetros. Os principais pontos incluem:

- **Folds de Dados**: São fornecidos à classe `Experimento` para realização de validação cruzada.
- **Método de Aprendizado de Máquina**: Pode ser um método genérico ou uma classe específica do `scikit-learn`.
- **Otimização de Hiperparâmetros**: Utiliza a biblioteca `Optuna` para otimizar os hiperparâmetros dos modelos.

### 2. Métodos de Aprendizado de Máquina

O arquivo `metodo.py` contém a definição das classes `MetodoAprendizadoDeMaquina` e `ScikitLearnAprendizadoDeMaquina`. A primeira é uma classe abstrata que define o método de aprendizado de máquina, enquanto a segunda implementa este método utilizando os recursos do `scikit-learn`.

### 3. Resultado e Fold

Os arquivos `resultado.py` contêm as definições das classes `Resultado` e `Fold`. A classe `Resultado` encapsula as métricas de avaliação do modelo, enquanto a classe `Fold` representa um conjunto de dados particionado para fins de treinamento e teste.

## Utilização

Para utilizar este projeto, siga estes passos:

1. **Configuração do Ambiente**: Certifique-se de ter todas as dependências instaladas. Você pode instalar as dependências listadas no arquivo `requirements.txt`.
   
2. **Execução dos Experimentos**: Crie instâncias da classe `Fold` com os dados apropriados e defina o método de aprendizado de máquina desejado. Em seguida, crie uma instância da classe `Experimento` e chame o método `resultados` para obter os resultados dos experimentos.

3. **Otimização de Hiperparâmetros** (opcional): Se desejar otimizar os hiperparâmetros do modelo, defina uma classe de otimização específica (por exemplo, `OtimizacaoObjetivoArvoreDecisao` ou `OtimizacaoObjetivoRandomForest`) e passe-a como argumento ao criar o objeto `Experimento`.

4. **Análise dos Resultados**: Analise os resultados obtidos, incluindo métricas de avaliação de desempenho como precisão, recall, F1-score, etc.

## Exemplo de Uso

Aqui está um exemplo de como usar este projeto:

```python
# Importações necessárias
import pandas as pd
from sklearn.tree import DecisionTreeClassifier
from experimento import Experimento, Fold, OtimizacaoObjetivoArvoreDecisao

# Dados de exemplo
df_treino = pd.read_csv('dados_treino.csv')
df_data_to_predict = pd.read_csv('dados_previsao.csv')
col_classe = 'classe'

# Definição dos folds de dados
folds = [...]

# Definição do método de aprendizado de máquina
ml_method = DecisionTreeClassifier()

# Otimização de hiperparâmetros (opcional)
classe_otimizacao = OtimizacaoObjetivoArvoreDecisao

# Criação e execução do experimento
experiment = Experimento(folds, ml_method, classe_otimizacao)
resultados = experiment.resultados

# Análise dos resultados
print("Métricas de Avaliação:")
for resultado in resultados:
    print(resultado)
```

## Contribuição

Contribuições são bem-vindas! Se você quiser contribuir para este projeto, por favor, abra uma issue para discutir suas ideias ou envie um pull request com suas alterações.

## Licença

Este projeto está licenciado sob a [MIT License](LICENSE).