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
# <a name="ltcommonbehaviorsgt"></a><span data-ttu-id="8afbb-102">&lt;commonBehaviors&gt;</span><span class="sxs-lookup"><span data-stu-id="8afbb-102">&lt;commonBehaviors&gt;</span></span>
<span data-ttu-id="8afbb-103">O `commonBehaviors` seção só pode ser definida no arquivo Machine. config.</span><span class="sxs-lookup"><span data-stu-id="8afbb-103">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="8afbb-104">Ele define duas coleções filhas nomeadas `endpointBehaviors` e `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="8afbb-104">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="8afbb-105">Cada coleção define elementos de comportamento consumidos por todos os [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] pontos de extremidade e serviços no computador respectivamente.</span><span class="sxs-lookup"><span data-stu-id="8afbb-105">Each collection defines behavior elements consumed by all [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] endpoints and services on the machine respectively.</span></span> <span data-ttu-id="8afbb-106">Comportamentos definidos no `endpointBehaviors` são aplicadas apenas a clientes e comportamentos definidos no `serviceBehaviors` são aplicadas apenas a serviços.</span><span class="sxs-lookup"><span data-stu-id="8afbb-106">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="8afbb-107">Se um comportamento é definido em `commonBehaviors` e `behaviors` seções, o comportamento de `behaviors` seção tem preferência.</span><span class="sxs-lookup"><span data-stu-id="8afbb-107">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
