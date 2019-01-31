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
# <a name="commonbehaviors"></a><span data-ttu-id="fb2ae-101">\<commonBehaviors></span><span class="sxs-lookup"><span data-stu-id="fb2ae-101">\<commonBehaviors></span></span>
<span data-ttu-id="fb2ae-102">O `commonBehaviors` seção só pode ser definida no arquivo Machine. config.</span><span class="sxs-lookup"><span data-stu-id="fb2ae-102">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="fb2ae-103">Ele define duas coleções filhas nomeadas `endpointBehaviors` e `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="fb2ae-103">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="fb2ae-104">Cada coleção define elementos de comportamento consumidos por todos os pontos de extremidade do WCF e serviços no computador, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="fb2ae-104">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span> <span data-ttu-id="fb2ae-105">Comportamentos definidos no `endpointBehaviors` são aplicadas apenas aos clientes e comportamentos definidos no `serviceBehaviors` são aplicadas apenas a serviços.</span><span class="sxs-lookup"><span data-stu-id="fb2ae-105">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="fb2ae-106">Se um comportamento é definido em ambos `commonBehaviors` e `behaviors` seções, o comportamento no `behaviors` seção é dada preferência.</span><span class="sxs-lookup"><span data-stu-id="fb2ae-106">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
