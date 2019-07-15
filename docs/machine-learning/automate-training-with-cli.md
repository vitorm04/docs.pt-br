---
title: Automatizar o treinamento de modelos com a CLI do ML.NET
description: Descubra como usar a ferramenta de CLI do ML.NET para treinar automaticamente o melhor modelo da linha de comando.
author: CESARDELATORRE
ms.date: 04/17/2019
ms.custom: how-to
ms.openlocfilehash: e5f75dc70ea5a76951d8698ea9c0d07cb2d4ddec
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663931"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a>Automatizar o treinamento de modelos com a CLI do ML.NET

A CLI do ML.NET "democratiza" o ML.NET, durante seu aprendizado, para desenvolvedores do .NET.

Para usar a API do ML.NET por si só (sem a CLI de AutoML do ML.NET), você precisa escolher um treinador (implementação de um algoritmo de aprendizado de máquina para uma tarefa específica) e o conjunto de transformações de dados (engenharia de recursos) para aplicar aos seus dados. O pipeline ideal variará para cada conjunto de dados e selecionar o algoritmo ideal entre todas as opções aumenta a complexidade. Além disso, cada algoritmo tem um conjunto de hiperparâmetros a serem ajustados. Portanto, você pode passar semanas e até meses em otimização de modelos de machine learning na tentativa de encontrar as combinações de engenharia de recursos, algoritmos de aprendizado e hiperparâmetros.

Esse processo pode ser automatizado com a CLI do ML.NET, que implementa o mecanismo inteligente AutoML do ML.NET.

> [!NOTE]
> Este tópico refere-se à **CLI** do ML.NET e ao **AutoML** do ML.NET, que estão atualmente em Versão Prévia. O material pode estar sujeito a alterações.

## <a name="what-is-the-mlnet-command-line-interface-cli"></a>O que é a CLI (interface de linha de comando) do ML.NET?

Você pode executar a CLI do ML.NET em qualquer prompt de comando (Windows, Mac ou Linux) para a geração de código-fonte e modelos do ML.NET de boa qualidade com base em seu conjunto de dados de treinamento.

Conforme mostrado na figura abaixo, é simples gerar um modelo de alta qualidade do ML.NET (arquivo. zip de modelo serializado) mais o código C# de exemplo para executar/pontuar esse modelo. Além disso, o código C# para criar/treinar esse modelo também é gerado, de modo que você pode pesquisar e iterar pelo algoritmo e pelas configurações usados para esse "melhor modelo" gerado.

![imagem](media/automate-training-with-cli/cli-high-level-process.png "Mecanismo AutoML funcionando dentro da CLI do ML.NET")

Você pode gerar esses ativos de seus próprios conjuntos de dados sem codificação por conta própria, portanto, ele também melhorará a sua produtividade, mesmo se você já conhecer o ML.NET.

Atualmente, as tarefas de ML compatíveis com a CLI do ML.NET são:

- `binary-classification`
- `multiclass-classification`
- `regression`
- Futuro: outras tarefas de aprendizado de máquina, tais como `recommendation`, `ranking`, `anomaly-detection` e `clustering`

Exemplo de uso:

```console
> mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

![imagem](media/automate-training-with-cli/cli-model-generation.gif)

Você pode executá-los do mesmo modo que no *Windows PowerShell*, no *bash do macOS/Linux ou no *CMD do Windows*. No entanto, o preenchimento automático de tabela (sugestões de parâmetro) não funcionará no *CMD do Windows*.

## <a name="output-assets-generated"></a>Ativos de saída gerados

O comando `auto-train` da CLI gera os seguintes ativos na pasta de saída:

- Um modelo .zip serializado ("melhor modelo") pronto para uso voltado à execução de previsões.
- Solução em C# com:
  - Código C# para a execução/pontuação que gerou o modelo (para fazer previsões em seus aplicativos do usuário final com esse modelo).
  - Código C# com o código de treinamento usado para gerar esse modelo (para fins de aprendizado ou retreinamento de modelo).
- Arquivo de log com informações de todas as iterações/varreduras entre vários algoritmos avaliados, incluindo sua configuração/pipeline detalhado.

Os primeiros dois ativos podem ser usados diretamente em seus aplicativos de usuário final (aplicativo Web ASP.NET Core, serviços, aplicativo da área de trabalho etc.) para fazer previsões com esse modelo de ML gerado.

O terceiro ativo, o código de treinamento, mostra a você qual código de API do ML.NET foi usado pela CLI para treinar o modelo gerado, de modo que você pode treinar novamente seu modelo e investigar e iterar em quais hiperparâmetros e treinador/algoritmo específicos foram selecionados pela CLI e AutoML nos bastidores.

## <a name="understanding-the-quality-of-the-model"></a>Noções básicas sobre a qualidade do modelo

Quando você gera um "melhor modelo" com a ferramenta da CLI, você vê métricas de qualidade (tais como precisão e R-quadrado) conforme apropriado para a tarefa de ML que você está usando como destino.

Aqui, resumiremos essas métricas agrupadas pela tarefa de ML para que você possa entender a qualidade do seu "melhor modelo" gerado automaticamente.

### <a name="metrics-for-binary-classification-models"></a>Métricas para modelos de classificação binária

A seguir, é exibida a lista de métricas de tarefas de classificação binária de ML para os cinco principais modelos encontrados pela CLI:

![imagem](media/automate-training-with-cli/cli-binary-classification-metrics.png)

A precisão é uma métrica popular para problemas de classificação, mas precisão nem sempre é a melhor métrica para selecionar o melhor modelo, conforme explicado nas referências abaixo. Há casos em que você precisa avaliar a qualidade do seu modelo com métricas adicionais.

Para explorar e entender as métricas que são produzidas como saída pela CLI, consulte [Métricas para classificação binária](resources/metrics.md#metrics-for-binary-classification).

### <a name="metrics-for-multi-class-classification-models"></a>Métricas para modelos de classificação multiclasse

A seguir é exibida a lista de métricas de tarefas de ML de classificação multiclasse para os cinco principais modelos encontrados pela CLI:

![imagem](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

Para explorar e entender as métricas que são produzidas pela CLI, consulte [Métricas para classificação multiclasse](resources/metrics.md#metrics-for-multi-class-classification).

### <a name="metrics-for-regression-models"></a>Métricas para modelos de regressão

Um modelo de regressão se ajustará bem aos dados se as diferenças entre os valores observados e os previstos do modelo forem pequenas e sem desvio. A regressão pode ser avaliada com certas métricas.

Você verá uma lista semelhante de métricas para os cinco modelos com melhor qualidade encontrados pela CLI. Neste caso em particular, relacionados a uma tarefa de ML de regressão:

![imagem](media/automate-training-with-cli/cli-regression-metrics.png)

Para explorar e entender as métricas que são produzidas pela CLI, consulte [Métricas para regressão](resources/metrics.md#metrics-for-regression).

## <a name="see-also"></a>Consulte também

- [Como instalar a ferramenta de CLI do ML.NET](how-to-guides/install-ml-net-cli.md)
- [Tutorial: Geração automática de um classificador binário usando a CLI do ML.NET](tutorials/mlnet-cli.md)
- [Referência de comandos da CLI do ML.NET](reference/ml-net-cli-reference.md)
- [Telemetria na CLI do ML.NET](resources/ml-net-cli-telemetry.md)
