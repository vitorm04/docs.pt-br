---
title: "Ação de conclusão da instância"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 83dec7ef4c911c0bca94caf7cc4c4bf832c8e1b6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="instance-completion-action"></a>Ação de conclusão da instância
O **ação de conclusão de instância** propriedade do repositório de instância de fluxo de trabalho de SQL permite que você especifique se os dados e metadados de instâncias de fluxo de trabalho é excluído do banco de dados de persistência depois de concluir as instâncias. Os valores permitidos para essa propriedade são **DeleteAll** e **DeleteNothing**. A lista a seguir descreve as opções:  
  
-   **DeleteAll (padrão).** Se o valor da propriedade é definido como DeleteAll, os dados e os metadados de instâncias de fluxo de trabalho são excluídos de base de dados de persistência depois que as instâncias são concluídas.  
  
-   **DeleteNothing.** Se o valor da propriedade é definida como DeleteNothing, os dados e os metadados de instâncias de fluxo de trabalho são mantidos na base de dados de persistência mesmo após as instâncias são concluídas.  
  
    > [!CAUTION]
    >  Mantendo informações de estado da instância depois que as instâncias são causas concluídas o base de dados de persistência crescer em tamanho. Como o tamanho de base de dados cresce as operações de base de dados que o subsistema de persistência executa levam mais tempo, portanto você precisa limpar periodicamente informações de estado da instância de base de dados de persistência para que os serviços executar a nível que satisfazem às suas necessidades de desempenho.
