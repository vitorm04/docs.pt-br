---
title: "Período viável de detecção de instâncias"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ea5c787-b638-47fd-bfc8-ede8c2898ce6
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2a78f8404d5e6b9d63c9455d059dcbb9a76f8c18
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="runnable-instances-detection-period"></a>Período viável de detecção de instâncias
A instância Store de fluxo de trabalho do SQL executa uma tarefa periodicamente interna que acorde e detecte instâncias praticáveis ou activatable na base de dados de persistência. O **período de detecção de instâncias executáveis** propriedade do repositório de instância de fluxo de trabalho SQL Especifica o período de tempo após o qual o armazenamento de instância de fluxo de trabalho do SQL executa uma tarefa de detecção para detectar qualquer fluxo de trabalho ativável ou executável instâncias do banco de dados de persistência após o ciclo de detecção anterior.  
  
 Definir um intervalo menor para essa propriedade reduz o tempo entre a validade de um timer associado com uma instância de fluxo de trabalho e a sinalização de evento e de carregamento de instância subsequente. No entanto, também aumenta a carga de processamento em um host e não pode ser desejável em situações onde timers e/ou falhas duráveis host são incomuns. O tipo de propriedade é período e o valor da propriedade segue o formato: hh:mm:ss. O valor mínimo para essa propriedade é 00:00:01. O valor padrão para a propriedade é 00:00:05.  
  
 Para obter mais informações consulte detectando e ativar instâncias de fluxo de trabalho executável e ativável [ativação de instância](../../../docs/framework/windows-workflow-foundation/instance-activation.md).
