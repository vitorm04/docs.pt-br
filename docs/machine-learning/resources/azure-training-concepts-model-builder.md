---
title: Recursos de treinamento do Construtor Modelo Azure
description: Um guia de recursos para o Azure Machine Learning
ms.topic: reference
ms.date: 02/27/2020
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: a19e13955d0eaea344109eb817f3a3959c3dd883
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185818"
---
# <a name="model-builder-azure-training-resources"></a>Recursos de treinamento do Construtor Modelo Azure

A seguir, um guia para ajudá-lo a aprender mais sobre os recursos usados para treinar modelos no Azure com o Model Builder.

## <a name="what-is-an-azure-machine-learning-experiment"></a>O que é um experimento de Machine Learning do Azure?

Um experimento de Aprendizado de Máquina do Azure é um recurso que precisa ser criado antes de executar o treinamento do Model Builder no Azure.

O experimento encapsula a configuração e os resultados para um ou mais treinamentos de aprendizado de máquina. Experimentos pertencem a um espaço de trabalho específico. A primeira vez que um experimento é criado, seu nome é registrado no espaço de trabalho. Quaisquer corridas subseqüentes - se o mesmo nome do experimento for usado - são registradas como parte do mesmo experimento. Caso contrário, um novo experimento é criado.

## <a name="what-is-an-azure-machine-learning-workspace"></a>O que é um espaço de trabalho de Machine Learning do Azure?

Um espaço de trabalho é um recurso de Machine Learning do Azure que fornece um lugar central para todos os recursos e artefatos de Machine Learning do Azure criados como parte do treinamento.

Para criar um espaço de trabalho de aprendizado de máquina do Azure, são necessários os seguintes:

- Nome: Um nome para o seu espaço de trabalho entre 3-33 caracteres. Os nomes só podem conter caracteres alfanuméricos e hífens.
- Região: A localização geográfica do data center para onde seu espaço de trabalho e recursos são implantados. Recomenda-se que você escolha um local próximo de onde você ou seus clientes estão.
- Grupo de recursos: Um contêiner que contém todos os recursos relacionados para uma solução Azure.

## <a name="what-is-an-azure-machine-learning-compute"></a>O que é um cálculo de Machine Learning do Azure?

Um azure Machine Learning é um VM Linux baseado em nuvem usado para treinamento.

Para criar um espaço de trabalho de aprendizado de máquina do Azure, são necessários os seguintes:

- Nome: Um nome para o seu espaço de trabalho entre 2-16 caracteres. Os nomes só podem conter caracteres alfanuméricos e hífens.
- Tamanho da computação

    O Model Builder pode usar um dos seguintes tipos de computação otimizados para GPU:

    | Tamanho | vCPU | Memória: GiB | Armazenamento temporário (SSD) GiB | GPU | Memória da GPU: GiB | Discos de dados máximos | Máximo de NICs |
    |---|---|---|---|---|---|---|---|
    | Standard_NC12   | 12 | 112 | 680  | 2 | 24 | 48 | 2 |
    | Standard_NC24   | 24 | 224 | 1440 | 4 | 48 | 64 | 4 |

    Visite a documentação do [NNc-series Linux VM](https://docs.microsoft.com/azure/virtual-machines/nc-series?toc=/azure/virtual-machines/linux/toc.json&bc=/azure/virtual-machines/linux/breadcrumb/toc.json) para obter mais detalhes sobre os tipos de computação otimizados para GPU.

## <a name="training"></a>Treinamento

O treinamento no Azure só está disponível para o cenário de classificação de imagem do Model Builder. O algoritmo usado para treinar esses modelos é uma Deep Neural Network baseada na arquitetura ResNet50. O processo de treinamento leva algum tempo e a quantidade de tempo pode variar dependendo do tamanho do cálculo selecionado, bem como da quantidade de dados. A primeira vez que um modelo é treinado, você pode esperar um tempo de treinamento um pouco maior porque os recursos têm que ser provisionados. Você pode acompanhar o progresso de suas corridas selecionando o link "Monitor atual executar no portal Azure" no Visual Studio.

## <a name="results"></a>Resultados

Uma vez que o treinamento é concluído, dois projetos são adicionados à sua solução com os seguintes sufixos:

- *ConsoleApp*: Um aplicativo de console C# .NET Core que fornece código inicial para construir o pipeline de previsão e fazer previsões.
- *Modelo*: A C# .NET Standard application que contém os modelos de dados que definem o esquema de dados do modelo de entrada e saída, bem como os seguintes ativos:

  - bestModel.onnx: Uma versão serializada do modelo no formato Open Neural Network Exchange (ONNX). ONNX é um formato de código aberto para modelos de IA que suporta interoperabilidade entre frameworks como ML.NET, PyTorch e TensorFlow.
  - bestModelMap.json: Uma lista de categorias usadas ao fazer previsões para mapear a saída do modelo para uma categoria de texto.
  - MLModel.zip: Uma versão serializada do pipeline de previsão de ML.NET que usa a versão serializada do `bestModelMap.json` modelo *bestModel.onnx* para fazer previsões e mapas de saídas usando o arquivo.

## <a name="use-the-machine-learning-model"></a>Use o modelo de aprendizado de máquina

As `ModelInput` `ModelOutput` aulas do projeto *Modelo* definem o esquema da entrada e saída esperadas do modelo, respectivamente.

Em um cenário de `ModelInput` classificação de imagem, o contém duas colunas:

- `ImageSource`: O caminho das cordas do local da imagem.
- `Label`: A categoria real a que a imagem pertence. `Label`é usado apenas como uma entrada no treinamento e não precisa ser fornecido ao fazer previsões.

O `ModelOutput` contém duas colunas:

- `Prediction`: A imagem é a categoria prevista.
- `Score`: A lista de probabilidades para todas as `Prediction`categorias (a mais alta pertence ao ).

## <a name="troubleshooting"></a>Solução de problemas

### <a name="cannot-create-compute"></a>Não é possível criar computação

Se ocorrer um erro durante a criação do cálculo do Azure Machine Learning, o recurso de computação ainda poderá existir, em um estado errado. Se você tentar recriar o recurso de computação com o mesmo nome, a operação falhará. Para corrigir esse erro:

- Crie a nova computação com um nome diferente
- Vá para o portal Azure e remova o recurso de computação original
