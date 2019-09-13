---
title: O que é o Construtor de Modelo e como ele funciona?
description: Como usar o Construtor de Modelo do ML.NET para treinar automaticamente um modelo de machine learning
author: natke
ms.date: 08/07/2019
ms.custom: overview
ms.openlocfilehash: 77b5e75fede1a4aa93eadcf7e21591d82f565cab
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929477"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a>O que é o Construtor de Modelo e como ele funciona?

O Construtor de Modelo do ML.NET é uma extensão gráfica do Visual Studio intuitiva para criar, treinar e implantar modelos de aprendizado de máquina personalizados.

O Construtor de Modelo usa o aprendizado de máquina automatizado (AutoML) para explorar os algoritmos diferentes de aprendizado de máquina e as configurações para ajudar você a encontrar o que melhor atende ao seu cenário.

Não é necessário ter experiência de aprendizado de máquina para usar o Construtor de Modelo. Você só precisa de um problema para resolver e alguns dados. O Construtor de Modelo gera o código para adicionar o modelo em seu aplicativo .NET.

![Animação de interface do usuário da extensão do Visual Studio do Construtor de Modelo](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> O Construtor de Modelo está atualmente na Versão Prévia.

## <a name="scenarios"></a>Cenários

Você pode trazer vários cenários diferentes para o Construtor de Modelo para gerar um modelo de machine learning para seu aplicativo.

Um cenário é uma descrição do tipo de previsão que você deseja fazer usando seus dados. Por exemplo:

- prever o volume de vendas futuras do produto com base em dados históricos de vendas
- classificar sentimentos como positivos ou negativos com base em revisões de cliente
- detectar se uma transação bancária é fraudulenta
- encaminhar problemas de comentários de clientes para a equipe correta em sua empresa

## <a name="choose-a-model-type"></a>Escolha um tipo de modelo

No Construtor de Modelos, é necessário selecionar um tipo de modelo de machine learning. O tipo de modelo depende de qual tipo de previsão você está tentando fazer.

Para cenários que preveem um número, o tipo de modelo de machine learning é chamado `regression`.

Para cenários que preveem uma categoria, o tipo de modelo é `classification`. Há dois tipos de classificação:

- em que há apenas duas categorias: `binary classification`.
- em que há apenas três ou mais categorias: `multiclass classification`.

### <a name="which-model-type-is-right-for-me"></a>Qual tipo de modelo é certo para mim?

#### <a name="predict-a-category-when-there-are-only-two-categories"></a>Prever uma categoria (quando há apenas duas categorias)

A classificação binária é usada para classificar dados em duas categorias (sim/não; aprovados/reprovados, verdadeiros/falsos; positivos/negativos).

![Diagrama mostrando exemplos de classificação binária incluindo detecção de fraude, mitigação de risco e triagem de aplicativo](media/binary-classification-examples.png)

A análise de sentimento pode ser usada para prever o sentimento positivo ou negativo de comentários do cliente. É um exemplo de tipo de modelo de classificação binária.

Se seu cenário exigir a classificação em duas categorias, você poderá usar esse modelo com seu próprio conjunto de dados.

#### <a name="predict-a-category-when-there-are-three-or-more-categories"></a>Prever uma categoria (quando há três ou mais categorias)

A classificação multiclasse pode ser usada para categorizar os dados em três ou mais classes. 

![Os exemplos de classificação multiclasse que incluem a classificação de documentos e de produtos, roteamento de tíquete de suporte e priorização de problemas do cliente](media/multiclass-classification-examples.png)

A classificação de problema pode ser usada para categorizar os problemas de comentários (por exemplo, sobre o GitHub) do cliente usando o título do problema e a descrição. É um exemplo do tipo de modelo de classificação multiclasse.

Você poderá usar o modelo de classificação do problema para seu cenário se quiser categorizar os dados em três ou mais categorias.

#### <a name="predict-a-number"></a>Prever um número

A regressão é usada para prever números.

![Diagrama mostrando exemplos de regressão, como a previsão de preços, a previsão de vendas e a manutenção preditiva](media/regression-examples.png)

A previsão de preço pode ser usada para prever preços de casas usando local, tamanho e outras características da casa. É um exemplo de um tipo de modelo de regressão.

Você poderá usar o modelo de previsão de preço para o seu cenário se quiser prever um valor numérico com seu próprio conjunto de dados.

#### <a name="custom-scenario-choose-your-model-type"></a>Cenário personalizado (escolha seu tipo de modelo)

O cenário personalizado permite que você escolha manualmente seu tipo de modelo.

## <a name="data"></a>Dados

Depois de escolher seu tipo de modelo, o Construtor de Modelos solicita que você forneça um conjunto de dados. Os dados são usados para treinar, avaliar e escolher o melhor modelo para seu cenário.

![Diagrama mostrando as etapas do Construtor de Modelos](media/model-builder-steps.png)

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

### <a name="example-datasets"></a>Conjuntos de dados de amostra

Se você ainda não tiver seus próprios dados, experimente um desses conjuntos de dados:

|Cenário|Tipo de modelo|Dados|Rotular|Recursos|
|-|-|-|-|-|
|Previsão de preço|Regressão|[dados de tarifas de táxi](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|Tarifa|Tempo da corrida, distância|
|Detecção de anomalias|Classificação binária|[dados de vendas do produto](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|Vendas do Produto|Month|
|Análise de Sentimento|Classificação binária|[dados de comentário do site](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|Rótulo (0 quando o sentimento é negativo, 1 quando é positivo)|Comentário, ano|
|Detecção de fraudes|Classificação binária|[dados do cartão de crédito](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|Classe (1 quando fraudulenta, caso contrário, 0)|Quantidade, V1-V28 (recursos anônimos)|
|Classificação de texto|Classificação multiclasse|[dados de problema do GitHub](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|Área|Título, Descrição|

## <a name="train"></a>Trem

Depois de selecionar seu cenário, dados e rótulo, o Construtor de Modelo treina o modelo.

### <a name="what-is-training"></a>O que é o treinamento?

O treinamento é um processo automático pelo qual Construtor de Modelo ensina seu modelo a responder perguntas para seu cenário. Depois de treinado, seu modelo pode fazer previsões com dados de entrada não vistos antes. Por exemplo, se estiver prevendo preços de casas e uma nova casa for oferecida no mercado, você poderá prever o preço de venda.

Como o Construtor de Modelo usa aprendizado de máquina automatizado (AutoML), ele não requer nenhuma entrada ou ajuste de você durante o treinamento.

## <a name="evaluate"></a>Avaliar o

A avaliação é o processo de usar o modelo treinado para fazer previsões com novos dados de teste e, em seguida, medir quão boas são as previsões.

O Construtor de Modelo divide os dados de treinamento em um conjunto de treinamento e um conjunto de teste. Os dados de treinamento (80%) são usados para treinar seu modelo e os dados de teste (20%) são retidos para avaliar seu modelo. O Construtor de Modelos usa métricas para medir a qualidade do modelo. As métricas específicas usadas dependem do tipo de modelo. Para obter mais informações, consulte [métricas de avaliação de modelo](resources/metrics.md).

## <a name="improve"></a>Aprimorar

Se a sua pontuação de desempenho do modelo não for tão boa quanto deseja, você poderá:

- Treinar por um período maior de tempo. Com mais tempo, usar o mecanismo de aprendizado de máquina automatizado para experimentar mais algoritmos e configurações.

- Adicionar mais dados. Às vezes, a quantidade de dados não é suficiente para treinar um modelo de machine learning de alta qualidade.

- Balancear seus dados. Para tarefas de classificação, certifique-se de que o conjunto de treinamento esteja equilibrado nas categorias. Por exemplo, se você tiver quatro classes para 100 exemplos de treinamento e as duas primeiras classes (tag1 e tag2) forem usadas para 90 registros, mas as outras duas (tag3 e tag4) forem usadas apenas nos 10 registros restantes, a falta de dados balanceados poderá fazer com que seu modelo tenha dificuldades para prever corretamente o tag3 ou o tag4.

## <a name="code"></a>Código

Após a fase de avaliação, o Construtor de Modelo gera um arquivo de modelo e o código que você pode usar para adicionar o modelo ao seu aplicativo. Modelos do ML.NET são salvos como um arquivo zip. O código para carregar e usar o modelo é adicionado como um novo projeto em sua solução. O Construtor de Modelo também adiciona um aplicativo de console de exemplo que você pode executar para ver seu modelo em ação.

Além disso, o Construtor de Modelo cria o código que gerou o modelo para que você possa entender as etapas usadas na geração do modelo. Você também pode usar o código de treinamento do modelo para treinar novamente seu modelo com novos dados.

## <a name="whats-next"></a>O que vem a seguir?

[Instalar](how-to-guides/install-model-builder.md) a extensão do Visual Studio do Construtor de Modelos

Experimente a [previsão de preço ou qualquer cenário de regressão](tutorials/predict-prices-with-model-builder.md)
