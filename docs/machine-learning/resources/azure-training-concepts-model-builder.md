---
title: Recursos de treinamento do Azure do Model Builder
description: Um guia de recursos para Azure Machine Learning
ms.topic: reference
ms.date: 02/25/2020
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: a0a75283cdc7402c67b6bfb0799189fa34cd39a7
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77675201"
---
# <a name="model-builder-azure-training-resources"></a>Recursos de treinamento do Azure do Model Builder

Veja a seguir um guia para ajudá-lo a saber mais sobre os recursos usados para treinar modelos no Azure com o construtor de modelos.

## <a name="what-is-an-azure-machine-learning-experiment"></a>O que é um experimento Azure Machine Learning?

Um experimento de Azure Machine Learning é um recurso que precisa ser criado antes de executar o treinamento do construtor de modelos no Azure.

O experimento encapsula a configuração e os resultados de uma ou mais execuções de treinamento do Machine Learning. Os experimentos pertencem a um espaço de trabalho específico. Na primeira vez que um experimento é criado, seu nome é registrado no espaço de trabalho. Qualquer execução subsequente – se o mesmo nome de experimento for usado-são registrados como parte do mesmo experimento. Caso contrário, um novo experimento será criado.

## <a name="what-is-an-azure-machine-learning-workspace"></a>O que é um espaço de trabalho Azure Machine Learning?

Um espaço de trabalho é um recurso Azure Machine Learning que fornece um local central para todos os Azure Machine Learning recursos e artefatos criados como parte da execução do treinamento.

Para criar um espaço de trabalho Azure Machine Learning, são necessários os seguintes:

- Nome: um nome para seu espaço de trabalho entre 3-33 caracteres. Os nomes só podem conter caracteres alfanuméricos e hifens. 
- Região: a localização geográfica do data center em que o espaço de trabalho e os recursos são implantados. É recomendável que você escolha um local perto de onde você ou seus clientes estão.
- Grupo de recursos: um contêiner que contém todos os recursos relacionados para uma solução do Azure.

## <a name="what-is-an-azure-machine-learning-compute"></a>O que é uma computação Azure Machine Learning?

Um Azure Machine Learning computação é uma VM Linux baseada em nuvem usada para treinamento.

Para criar um espaço de trabalho Azure Machine Learning, são necessários os seguintes:

- Nome: um nome para seu espaço de trabalho entre 2-16 caracteres. Os nomes só podem conter caracteres alfanuméricos e hifens.
- Tamanho da computação

    O construtor de modelos pode usar um dos seguintes tipos de computação otimizados para GPU:

    | Tamanho | vCPU | Memória: GiB | Armazenamento temporário (SSD) GiB | GPU | Memória da GPU: GiB | Discos de dados máximos | Máximo de NICs |
    |---|---|---|---|---|---|---|---|
    | Standard_NC12   | 12 | 112 | 680  | 2 | 24 | 48 | 2 |
    | Standard_NC24   | 24 | 224 | 1440 | 4 | 48 | 64 | 4 |

    Visite a [documentação da VM do Linux da série NC](https://docs.microsoft.com/azure/virtual-machines/nc-series?toc=/azure/virtual-machines/linux/toc.json&bc=/azure/virtual-machines/linux/breadcrumb/toc.json) para obter mais detalhes sobre tipos de computação otimizados para GPU.

## <a name="training"></a>Treinamento

O treinamento no Azure só está disponível para o cenário de classificação de imagem do construtor de modelos. O algoritmo usado para treinar esses modelos é uma rede neural profunda baseada na arquitetura ResNet50. Durante o treinamento, os recursos necessários para treinar o modelo são provisionados e o modelo é treinado. Esse processo leva vários minutos e a quantidade de tempo pode variar dependendo do tamanho da computação selecionada, bem como da quantidade de dados. Você pode acompanhar o progresso de suas execuções selecionando o link "monitorar a execução atual no portal do Azure" no Visual Studio.

## <a name="results"></a>Resultados

Quando o treinamento for concluído, dois projetos serão adicionados à sua solução com os seguintes sufixos:

- *ConsoleApp*: um C# aplicativo de console .NET Core que fornece o código inicial para criar o pipeline de previsão e fazer previsões.
- *Modelo*: um C# aplicativo .net standard que contém os modelos de dados que definem o esquema de dados de modelo de entrada e saída, bem como os seguintes ativos:

  - bestModel. onnx: uma versão serializada do modelo em formato de intercâmbio de rede neural aberto (ONNX). ONNX é um formato de software livre para modelos de ia que oferece suporte à interoperabilidade entre estruturas como ML.NET, PyTorch e TensorFlow.
  - bestModelMap. JSON: uma lista de categorias usadas ao fazer previsões para mapear a saída do modelo para uma categoria de texto.
  - MLModel. zip: uma versão serializada do pipeline de previsão ML.NET que usa a versão serializada do modelo *bestModel. onnx* para fazer previsões e mapeia saídas usando o arquivo `bestModelMap.json`.
  
## <a name="troubleshooting"></a>solução de problemas

### <a name="cannot-create-compute"></a>Não é possível criar computação

Se ocorrer um erro durante a criação de computação Azure Machine Learning, o recurso de computação ainda poderá existir, em um estado com erros. Se você tentar recriar o recurso de computação com o mesmo nome, a operação falhará. Para corrigir esse erro:

* Criar a nova computação com um nome diferente
* Vá para a portal do Azure e remova o recurso de computação original
