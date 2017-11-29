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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4d1e0f367ef167e5bf47d0936e0b3200ca7dbe19
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="instance-completion-action"></a>Ação de conclusão da instância
O **ação de conclusão de instância** propriedade do repositório de instância de fluxo de trabalho de SQL permite que você especifique se os dados e metadados de instâncias de fluxo de trabalho é excluído do banco de dados de persistência depois de concluir as instâncias. Os valores permitidos para essa propriedade são **DeleteAll** e **DeleteNothing**. A lista a seguir descreve as opções:  
  
-   **DeleteAll (padrão).** Se o valor da propriedade é definido como DeleteAll, os dados e os metadados de instâncias de fluxo de trabalho são excluídos de base de dados de persistência depois que as instâncias são concluídas.  
  
-   **DeleteNothing.** Se o valor da propriedade é definida como DeleteNothing, os dados e os metadados de instâncias de fluxo de trabalho são mantidos na base de dados de persistência mesmo após as instâncias são concluídas.  
  
    > [!CAUTION]
    >  Mantendo informações de estado da instância depois que as instâncias são causas concluídas o base de dados de persistência crescer em tamanho. Como o tamanho de base de dados cresce as operações de base de dados que o subsistema de persistência executa levam mais tempo, portanto você precisa limpar periodicamente informações de estado da instância de base de dados de persistência para que os serviços executar a nível que satisfazem às suas necessidades de desempenho.
