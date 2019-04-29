---
title: <commonBehaviors>
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: 73bf759fd3dfa87398aa74de93160a4ffce08eba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704356"
---
# <a name="commonbehaviors"></a>\<commonBehaviors>
O `commonBehaviors` seção só pode ser definida no arquivo Machine. config. Ele define duas coleções filhas nomeadas `endpointBehaviors` e `serviceBehaviors`.  Cada coleção define elementos de comportamento consumidos por todos os pontos de extremidade do WCF e serviços no computador, respectivamente. Comportamentos definidos no `endpointBehaviors` são aplicadas apenas aos clientes e comportamentos definidos no `serviceBehaviors` são aplicadas apenas a serviços. Se um comportamento é definido em ambos `commonBehaviors` e `behaviors` seções, o comportamento no `behaviors` seção é dada preferência.
