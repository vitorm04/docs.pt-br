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
# <a name="commonbehaviors"></a><span data-ttu-id="156a6-101">\<commonBehaviors></span><span class="sxs-lookup"><span data-stu-id="156a6-101">\<commonBehaviors></span></span>
<span data-ttu-id="156a6-102">O `commonBehaviors` seção só pode ser definida no arquivo Machine. config.</span><span class="sxs-lookup"><span data-stu-id="156a6-102">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="156a6-103">Ele define duas coleções filhas nomeadas `endpointBehaviors` e `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="156a6-103">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="156a6-104">Cada coleção define elementos de comportamento consumidos por todos os pontos de extremidade do WCF e serviços no computador, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="156a6-104">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span> <span data-ttu-id="156a6-105">Comportamentos definidos no `endpointBehaviors` são aplicadas apenas aos clientes e comportamentos definidos no `serviceBehaviors` são aplicadas apenas a serviços.</span><span class="sxs-lookup"><span data-stu-id="156a6-105">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="156a6-106">Se um comportamento é definido em ambos `commonBehaviors` e `behaviors` seções, o comportamento no `behaviors` seção é dada preferência.</span><span class="sxs-lookup"><span data-stu-id="156a6-106">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
