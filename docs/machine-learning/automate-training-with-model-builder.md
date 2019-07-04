---
title: O que é o Construtor de Modelo e como ele funciona?
description: Como usar o Construtor de Modelo do ML.NET para treinar automaticamente um modelo de machine learning
author: natke
ms.date: 06/26/2019
ms.custom: overview
ms.openlocfilehash: 6f5bbe3c389e3ca42550a48ef3e6edbc963ac2e9
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410584"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a>O que é o Construtor de Modelo e como ele funciona?

O Construtor de Modelo do ML.NET é uma extensão gráfica do Visual Studio fácil de entender para compilar, treinar e implantar modelos de aprendizado de máquina personalizados. 

O Construtor de Modelo usa o aprendizado de máquina automatizado (AutoML) para explorar os algoritmos diferentes de aprendizado de máquina e as configurações para ajudar você a encontrar o que melhor atende ao seu cenário.

Não é necessário ter experiência de aprendizado de máquina para usar o Construtor de Modelo. Você só precisa de um problema para resolver e alguns dados. O Construtor de Modelo gera o código para adicionar o modelo em seu aplicativo .NET.

![Animação de interface do usuário da extensão do Visual Studio do Construtor de Modelo](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> O Construtor de Modelo está atualmente na Versão Prévia.

## <a name="scenarios"></a>Cenários

Você pode trazer vários cenários diferentes para o Construtor de Modelo para gerar um modelo de machine learning para seu aplicativo.

Um cenário é uma descrição do tipo de previsão que você deseja fazer em seus dados. Por exemplo:
- prever o volume de vendas futuras do produto com base em dados históricos de vendas
- classificar sentimentos como positivos ou negativos com base em revisões de cliente
- detectar se uma transação bancária é fraudulenta
- encaminhar problemas de comentários de clientes para a equipe correta em sua empresa

No Construtor de Modelo, você deve mapear seu cenário para uma [tarefa do ML.NET](resources/tasks.md). Você pode usar o construtor de modelo para **regressão** (prevendo números) e **classificação** (prevendo categorias).

### <a name="which-machine-learning-scenario-is-right-for-me"></a>Qual cenário do aprendizado de máquina é adequado para mim?

O Construtor de Modelos é fornecido com modelos de análise de sentimento, classificação de problema, previsão de preço e cenários personalizados. Esses modelos podem ser usados como ponto de partida para o cenário do ML.NET específico.

#### <a name="sentiment-analysis-binary-classification"></a>Análise de sentimento (classificação binária)

A análise de sentimento pode ser usada para prever o sentimento positivo ou negativo de comentários do cliente. É um exemplo da tarefa de classificação binária.

A classificação binária é usada para classificar dados em duas classes (sim/não; aprovados/reprovados, verdadeiros/falsos; positivos/negativos). Pode ser usada para responder a perguntas como:

- Esse email é um spam? (detecção de spam)
- Quais candidatos podem ser elegíveis para a associação? (triagem do aplicativo)
- Quais contas podem não pagar suas faturas a tempo? (mitigação de risco)
- Essa transação de cartão de crédito é fraudulenta? (detecção de fraude)

Se seu cenário exigir a classificação em duas categorias, você poderá usar esse modelo com seu próprio conjunto de dados.
 
#### <a name="issue-classification-multiclass-classification"></a>Classificação de problemas (classificação multiclasse)

A classificação de problema pode ser usada para categorizar os problemas de comentários (por exemplo, sobre o GitHub) do cliente usando o título do problema e a descrição. É um exemplo da tarefa de classificação multiclasse.

A classificação multiclasse pode ser usada para categorizar os dados em três ou mais classes. Pode ser usada para responder a perguntas como:

- Para qual departamento devo rotear um tíquete de suporte? (roteamento de tíquete de suporte)
- O que é a prioridade de um problema do cliente? (priorização de problema do cliente)
- A qual categoria um produto pertence? (classificação de produto)
- Qual é o tipo de documento? (classificação de documento/email)

Você poderá usar o modelo de classificação do problema para seu cenário se quiser categorizar os dados em três ou mais categorias.

#### <a name="price-prediction-regression"></a>Previsão de preços (regressão)

A previsão de preço pode ser usada para prever preços de casas usando local, tamanho e outras características da casa. É um exemplo de tarefa de regressão.

A regressão é usada para prever números. Pode ser usada para responder a perguntas como:

- Por qual preço uma casa será vendida? (previsão de preço)
- Depois de quanto tempo uma peça mecânica requer manutenção? (manutenção preditiva)
- Qual é o teor de umidade neste secador? (monitoramento de máquina)
- Qual será o total anual de vendas para esta região? (previsão de vendas)

Você poderá usar o modelo de previsão de preço para o seu cenário se quiser prever um valor numérico com seu próprio conjunto de dados.

#### <a name="custom-scenario-choose-your-task"></a>Cenário personalizado (escolha sua tarefa)

O cenário personalizado permite que você escolha sua própria tarefa. Escolha o cenário que faz mais sentido para o seu problema.

O cenário personalizado permite que você escolha sua própria tarefa de aprendizado de máquina. Em modelos anteriores, a tarefa de aprendizado de máquina foi corrigida para o cenário: classificação binária, classificação multiclasse ou regressão. Neste modelo, você pode escolher a tarefa de ML que deseja usar em seus dados.

## <a name="data"></a>Dados

Depois de mapear seu cenário para uma tarefa, o Construtor de Modelo solicita que você forneça um conjunto de dados. Os dados são usados para treinar, avaliar e escolher o melhor modelo para seu cenário. Você também precisa escolher a saída que deseja prever.

### <a name="choose-the-output-to-predict-label"></a>Escolha a saída para prever (rótulo)

Um conjunto de dados é uma tabela de linhas de exemplos de treinamento e colunas de atributos. Cada linha tem:
- um **rótulo** (o atributo que você deseja prever)
- **recursos** (atributos que são usados como entradas para prever o rótulo).

Para o cenário de previsão do preço das casas, os recursos podem ser:
- os metros quadrados da casa
- o número de quartos e banheiros
- o código postal

O rótulo é o preço histórico de casas para essa linha de valores de metro quadrado, quarto e banheiro e código postal.

![Tabela mostrando linhas e colunas de dados de preços de casas com recursos que consistem em quartos de tamanho de código postal e etiqueta de preço](media/model-builder-data.png)

### <a name="data-formats"></a>Formatos de dados

O Construtor de Modelo coloca as seguintes limitações nos dados:

- Os dados devem ser armazenados em um arquivo (.csv ou .tsv com uma linha de cabeçalho) ou em um banco de dados do SQL server.
- Um limite de 1 GB no conjunto de dados de treinamento
- O SQL Server tem um limite de 100 mil linhas para treinamento
- Os dados do SQL Server são copiados do servidor para seu computador local antes do treinamento

### <a name="example-datasets"></a>Conjuntos de dados de amostra

Se você ainda não tiver seus próprios dados, experimente um desses conjuntos de dados:

|Cenário|Tarefa de ML|Dados|Rotular|Recursos|
|-|-|-|-|-|
|Previsão de preço|regressão|[dados de tarifas de táxi](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|Tarifa|Tempo da corrida, distância|
|Detecção de anomalias|classificação binária|[dados de vendas do produto](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|Vendas do Produto|Mês|
|Análise de sentimento|classificação binária|[dados de comentário do site](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_SentimentAnalysis/SentimentAnalysis/Data/wikiDetoxAnnotated40kRows.tsv)|Rótulo (0 quando o sentimento é negativo, 1 quando é positivo)|Comentário, ano|
|Detecção de fraude|classificação binária|[dados do cartão de crédito](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|Classe (1 quando fraudulenta, caso contrário, 0)|Quantidade, V1-V28 (recursos anônimos)|
|Classificação de texto|classificação multiclasse|[dados de problema do GitHub](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|Área|Título, Descrição|

## <a name="train"></a>Treinar

Depois de selecionar seu cenário, dados e rótulo, o Construtor de Modelo treina o modelo.

### <a name="what-is-training"></a>O que é o treinamento?

O treinamento é um processo automático pelo qual Construtor de Modelo ensina seu modelo a responder perguntas para seu cenário. Depois de treinado, seu modelo pode fazer previsões com dados de entrada não vistos antes. Por exemplo, se estiver prevendo preços de casas e uma nova casa for oferecida no mercado, você poderá prever o preço de venda.

Como o Construtor de Modelo usa aprendizado de máquina automatizado (AutoML), ele não requer nenhuma entrada ou ajuste de você durante o treinamento.

### <a name="how-long-should-i-train-for"></a>Por quanto tempo devo treinar?

Você pode oferecer um tempo de treinamento. Em geral, treinamento por mais tempo produz um modelo mais preciso. Mais tempo de treinamento também é necessário na medida em que o tamanho do conjunto de dados de treinamento aumenta. A tabela a seguir fornece algumas diretrizes de tempo de treinamento para conjuntos de dados de tamanho maior.

Tamanho do conjunto de dados  | Tipo de conjunto de dados       | Média Hora de treinar
------------- | ------------------ | --------------
0 a 10 Mb     | Numérico e texto   | 10 s
10 a 100 Mb   | Numérico e texto   | 10 min 
100 a 500 Mb  | Numérico e texto   | 30 min 
500 a 1 Gb    | Numérico e texto   | 60 min 
Mais de 1 Gb         | Numérico e texto   | Mais de 3 horas 

O tempo exato para treinar também depende:

- do tipo de colunas, ou seja, texto vs números
- do tipo de tarefa de aprendizado de máquina (regressão ou classificação)
- do número de linhas usadas para treinamento
- do número de colunas de recursos usadas para treinamento

O Construtor de Modelo foi testado para escalar com um conjunto de dados de 1 TB, mas a criação de um modelo de alta qualidade para o tamanho do conjunto de dados pode levar até quatro dias!

## <a name="evaluate"></a>Avaliar o

A avaliação é o processo de usar o modelo treinado para fazer previsões com novos dados de teste e, em seguida, medir quão boas são as previsões.

O Construtor de Modelo divide os dados de treinamento em um conjunto de treinamento e um conjunto de teste. Os dados de treinamento (80%) são usados para treinar seu modelo e os dados de teste (20%) são retidos para avaliar seu modelo.  As métricas usadas para avaliação dependem da tarefa de ML. Para obter mais informações, consulte [métricas de avaliação de modelo](resources/metrics.md).  

### <a name="sentiment-analysis-binary-classification"></a>Análise de sentimento (classificação binária)

A métrica padrão para problemas de classificação binária é a **precisão**. A precisão define a proporção de previsões corretas feitas pelo seu modelo sobre o conjunto de dados de teste. Quanto **mais próximo de 100, melhor**.

Outras métricas relatadas, como AUC (Área sob a curva), que mede a taxa positiva verdadeira versus a taxa de falsos positivos, devem ser maiores que 0,50 para que os modelos sejam aceitáveis. 

Métricas adicionais, como a pontuação F1, podem ser usadas para controlar o equilíbrio entre a precisão (proporção de previsões corretas e as previsões totais dessa classe) e o recall (proporção de previsões corretas para o total de membros reais dessa classe).

### <a name="issue-classification-multiclass-classification"></a>Classificação de problemas (classificação multiclasse)

A métrica padrão para problemas de classificação multiclasse é a **microprecisão**. Quanto **mais próximo de 100, melhor**.

Para problemas em que os dados são categorizados em várias classes, há dois tipos de precisão:

- Microprecisão: a fração de previsões corretas em todas as instâncias. No cenário de problema de classificação, a microprecisão é a proporção dos problemas de entrada que são atribuídos à categoria correta. 
- Precisão macro é a precisão média no nível de classe. No cenário de classificação de problema, a precisão é medida para cada categoria, então as precisões de categoria estão na média. Para esta métrica, todas as classes recebem o mesmo peso. Para conjuntos de dados perfeitamente balanceados (onde há um número igual de exemplos de cada categoria), a microprecisão e a macroprecisão são iguais.


### <a name="price-prediction-regression"></a>Previsão de preços (regressão)

A métrica padrão para problemas de regressão é **RSquared**. 1 é o melhor valor possível. Quanto mais próximo o RSquared estiver de 1, melhor será seu modelo.

Outras métricas relatadas, como perda absoluta, perda quadrática e perda de RMS, podem ser usadas para entender seu modelo e compará-lo com outros modelos de regressão. 

## <a name="improve"></a>Aprimorar

Se a sua pontuação de desempenho do modelo não for tão boa quanto deseja, você poderá:

* Treinar por um período maior de tempo. Com mais tempo, usar o mecanismo de aprendizado de máquina automatizado para experimentar mais algoritmos e configurações.

* Adicionar mais dados. Às vezes, a quantidade de dados não é suficiente para treinar um modelo de machine learning de alta qualidade. 

* Balancear seus dados. Para tarefas de classificação, certifique-se de que o conjunto de treinamento esteja equilibrado nas categorias. Por exemplo, se você tiver quatro classes para 100 exemplos de treinamento e as duas primeiras classes (tag1 e tag2) forem usadas para 90 registros, mas as outras duas (tag3 e tag4) forem usadas apenas nos 10 registros restantes, a falta de dados balanceados poderá fazer com que seu modelo tenha dificuldades para prever corretamente o tag3 ou o tag4.

## <a name="code"></a>Código

Após a fase de avaliação, o Construtor de Modelo gera um arquivo de modelo e o código que você pode usar para adicionar o modelo ao seu aplicativo. Modelos do ML.NET são salvos como um arquivo zip. O código para carregar e usar o modelo é adicionado como um novo projeto em sua solução. O Construtor de Modelo também adiciona um aplicativo de console de exemplo que você pode executar para ver seu modelo em ação.

Além disso, o Construtor de Modelo cria o código que gerou o modelo para que você possa entender as etapas usadas na geração do modelo. Você também pode usar o código de treinamento do modelo para treinar novamente seu modelo com novos dados.

## <a name="whats-next"></a>O que vem a seguir?

Experimente a [previsão de preço ou qualquer cenário de regressão](tutorials/predict-prices-with-model-builder.md)
