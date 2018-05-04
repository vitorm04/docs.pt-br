---
title: '&lt;commonBehaviors&gt;'
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: aaf89f73b6de250aaa572b8fef31e5a1ebd5482b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltcommonbehaviorsgt"></a>&lt;commonBehaviors&gt;
O `commonBehaviors` seção só pode ser definida no arquivo Machine. config. Ele define duas coleções filhas nomeadas `endpointBehaviors` e `serviceBehaviors`.  Cada coleção define elementos de comportamento consumidos por todos os [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] pontos de extremidade e serviços no computador respectivamente. Comportamentos definidos no `endpointBehaviors` são aplicadas apenas a clientes e comportamentos definidos no `serviceBehaviors` são aplicadas apenas a serviços. Se um comportamento é definido em `commonBehaviors` e `behaviors` seções, o comportamento de `behaviors` seção tem preferência.
