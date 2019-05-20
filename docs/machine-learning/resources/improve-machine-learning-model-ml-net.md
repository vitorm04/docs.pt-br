---
title: 'Como fazer: Melhorar a precisão do modelo'
description: Saiba como melhorar a precisão do modelo
ms.date: 04/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc
ms.openlocfilehash: 8bb47102ede8e135090b1381eb815dccd512e03d
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557791"
---
# <a name="improve-mlnet-model-accuracy"></a>Melhorar a precisão do modelo do ML.NET

Saiba como melhorar a precisão do seu modelo.

## <a name="reframe-the-problem"></a>Reestruture o problema

Às vezes, melhorar um modelo pode não ter nenhuma relação com os dados ou as técnicas usados para treinar o modelo. Em vez disso, talvez apenas a pergunta errada esteja sendo feita. Considere examinar o problema de ângulos diferentes e aproveitar os dados para extrair indicadores latentes e relações ocultas para refinar a pergunta.

## <a name="provide-more-data-samples"></a>Fornecer mais amostras de dados

Como os seres humanos, quanto mais os algoritmos de treinamento obtêm, maior é a probabilidade de um melhor desempenho. Uma maneira de melhorar o desempenho do modelo é fornecer mais exemplos de dados de treinamento para os algoritmos. Quanto mais dados ele usa para aprender, mais casos ele é capaz de identificar corretamente.

## <a name="add-context-to-the-data"></a>Adicionar contexto aos dados

O significado de um único ponto de dados pode ser difícil de interpretar. Criar contexto em torno dos pontos de dados ajuda os algoritmos, bem como os especialistas no assunto, a tomar decisões melhores. Por exemplo, o fato de que uma casa tem três quartos não dá, isoladamente, uma boa indicação de seu preço. No entanto, se você adicionar contexto e agora souber que ela está em um ambiente suburbano fora de uma grande área metropolitana em que a idade média é de 38, a renda familiar média é de 80.000 USD e as escolas estão no 20º percentil superior, o algoritmo terá mais informações nas quais basear suas decisões. Todo esse contexto pode ser adicionado como entrada para o modelo de machine learning como recursos.

## <a name="use-meaningful-data-and-features"></a>Usar os recursos e dados significativos

Embora mais exemplos de dados e recursos possam ajudar a melhorar a precisão do modelo, também podem introduzir ruído, já que nem todos os dados e recursos são significativos. Portanto, é importante entender quais recursos são os que mais afetam as decisões tomadas pelo algoritmo. Usar técnicas como PFI (Importância de Recurso de Permutação) pode ajudar a identificar os principais recursos, e não apenas ajudar a explicar o modelo, como também usar a saída como um método de seleção de recurso para reduzir a quantidade de recursos com ruídos que entram no processo de treinamento.

Saiba como usar PFI acessando o seguinte [link](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md)

## <a name="cross-validation"></a>Validação cruzada

A validação cruzada é uma técnica de avaliação de modelo e treinamento que divide os dados em várias partições e treina vários algoritmos nessas partições. Essa técnica melhora a robustez do modelo mantendo os dados do processo de treinamento. Além de melhorar o desempenho em observações não vistas, em ambientes com restrições de dados, pode ser uma ferramenta eficiente para treinar modelos com um conjunto de dados menor.

Acesse o link a seguir para saber mais sobre [como usar a validação cruzada no ML.NET](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md)

## <a name="hyperparameter-tuning"></a>Ajuste de hiperparâmetro

Treinar modelos de machine learning é um processo iterativo e exploratório. Por exemplo, qual é o número ideal de clusters ao treinar um modelo usando o algoritmo K-Means? A resposta depende de muitos fatores, como a estrutura dos dados. Encontrar esse número exigiria experimentar diferentes valores de k e, em seguida, avaliar o desempenho para determinar qual valor é melhor. A prática de ajustar esses parâmetros para localizar um modelo ideal é conhecida como ajuste de hiperparâmetros.

## <a name="choose-a-different-algorithm"></a>Escolher um algoritmo diferente

Tarefas de aprendizado de máquina, como a regressão e classificação, contêm várias implementações de algoritmo. Talvez o problema que você está tentando resolver e a maneira como seus dados estão estruturados não sejam adequados para o algoritmo atual. Nesse caso, considere usar um algoritmo diferente para a tarefa para ver se ele aprende melhor com seus dados.

O link a seguir fornece mais [orientações sobre qual algoritmo escolher](../how-to-choose-an-ml-net-algorithm.md).
