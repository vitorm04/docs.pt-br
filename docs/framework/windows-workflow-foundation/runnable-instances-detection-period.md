---
title: Período viável de detecção de instâncias
ms.date: 03/30/2017
ms.assetid: 4ea5c787-b638-47fd-bfc8-ede8c2898ce6
ms.openlocfilehash: 7b12353c3bd18367618825d22d020391b14ec3f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513231"
---
# <a name="runnable-instances-detection-period"></a>Período viável de detecção de instâncias
A instância Store de fluxo de trabalho do SQL executa uma tarefa periodicamente interna que acorde e detecte instâncias praticáveis ou activatable na base de dados de persistência. O **período de detecção de instâncias executáveis** propriedade do repositório de instância de fluxo de trabalho SQL Especifica o período de tempo após o qual o armazenamento de instância de fluxo de trabalho do SQL executa uma tarefa de detecção para detectar qualquer fluxo de trabalho ativável ou executável instâncias do banco de dados de persistência após o ciclo de detecção anterior.  
  
 Definir um intervalo menor para essa propriedade reduz o tempo entre a validade de um timer associado com uma instância de fluxo de trabalho e a sinalização de evento e de carregamento de instância subsequente. No entanto, também aumenta a carga de processamento em um host e não pode ser desejável em situações onde timers e/ou falhas duráveis host são incomuns. O tipo de propriedade é período e o valor da propriedade segue o formato: hh:mm:ss. O valor mínimo para essa propriedade é 00:00:01. O valor padrão para a propriedade é 00:00:05.  
  
 Para obter mais informações consulte detectando e ativar instâncias de fluxo de trabalho executável e ativável [ativação de instância](../../../docs/framework/windows-workflow-foundation/instance-activation.md).
