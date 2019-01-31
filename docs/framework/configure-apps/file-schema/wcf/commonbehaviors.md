---
title: <commonBehaviors>
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: 73bf759fd3dfa87398aa74de93160a4ffce08eba
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268750"
---
# <a name="commonbehaviors"></a>\<commonBehaviors>
O `commonBehaviors` seção só pode ser definida no arquivo Machine. config. Ele define duas coleções filhas nomeadas `endpointBehaviors` e `serviceBehaviors`.  Cada coleção define elementos de comportamento consumidos por todos os pontos de extremidade do WCF e serviços no computador, respectivamente. Comportamentos definidos no `endpointBehaviors` são aplicadas apenas aos clientes e comportamentos definidos no `serviceBehaviors` são aplicadas apenas a serviços. Se um comportamento é definido em ambos `commonBehaviors` e `behaviors` seções, o comportamento no `behaviors` seção é dada preferência.
