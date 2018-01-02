---
title: '&lt;commonBehaviors&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9b39942cc438201ceaecf1fee62ce3fefdc27b68
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcommonbehaviorsgt"></a>&lt;commonBehaviors&gt;
O `commonBehaviors` seção só pode ser definida no arquivo Machine. config. Ele define duas coleções filhas nomeadas `endpointBehaviors` e `serviceBehaviors`.  Cada coleção define elementos de comportamento consumidos por todos os [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] pontos de extremidade e serviços no computador respectivamente. Comportamentos definidos no `endpointBehaviors` são aplicadas apenas a clientes e comportamentos definidos no `serviceBehaviors` são aplicadas apenas a serviços. Se um comportamento é definido em `commonBehaviors` e `behaviors` seções, o comportamento de `behaviors` seção tem preferência.
