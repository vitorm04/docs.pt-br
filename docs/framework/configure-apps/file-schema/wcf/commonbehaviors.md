---
title: <commonBehaviors>
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: 55f70157b6759c5e1cb45da20eed928fa1d4a183
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176052"
---
# \<commonBehaviors>

A `commonBehaviors` seção só pode ser definida no arquivo de machine.config. Ele define duas coleções filho chamadas `endpointBehaviors` e `serviceBehaviors` .  Cada coleção define elementos de comportamento consumidos por todos os pontos de extremidade do WCF e serviços no computador, respectivamente. Os comportamentos definidos em `endpointBehaviors` são aplicados somente aos clientes, e os comportamentos definidos no `serviceBehaviors` são aplicados somente aos serviços. Se um comportamento for definido em ambas `commonBehaviors` as `behaviors` seções e, o comportamento na `behaviors` seção terá preferência.
