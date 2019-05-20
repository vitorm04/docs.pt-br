---
title: Aprendizado de máquina automatizado com o ML.NET
description: Visão geral do treinamento e seleção automáticos de modelos
author: natke
ms.date: 05/01/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
ms.openlocfilehash: e6654718f174c9d8b628b05d85d74952c222eb66
ms.sourcegitcommit: 4c10802ad003374641a2c2373b8a92e3c88babc8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65452738"
---
# <a name="automated-machine-learning-with-mlnet"></a>Aprendizado de máquina automatizado com o ML.NET

O aprendizado de máquina automatizado é um recurso do ML.NET que executa a seleção e treinamento automáticos de modelos. Você especifica a tarefa de aprendizado de máquina e fornece um conjunto de dados. O ML automatizado escolhe o modelo com as melhores métricas. Ele produz:
- um arquivo de modelo que pode ser carregado em seu aplicativo de previsão
- código do aplicativo para fazer previsões
- o código-fonte usado para seleção de recursos e o treinamento do modelo (para entender o modelo)

> [!NOTE]
> Esse recurso está atualmente em versão prévia e o material pode estar sujeito a alterações. 

O ML automatizado é atualmente limitado a [tarefas](resources/tasks.md) de aprendizado de máquina de classificação binária, classificação multiclasse e regressão. As outras tarefas de aprendizado de máquina terão suporte em versões futuras.

Há três maneiras de usar o ML automatizado:
1. Na linha de comando, com a [CLI do ML.NET](automate-training-with-cli.md)
1. Por meio de um aplicativo com a [API de ML automatizada](how-to-guides/how-to-use-the-automl-api.md)
1. Com uma interface gráfica do usuário, com o construtor de modelo do ML.NET
