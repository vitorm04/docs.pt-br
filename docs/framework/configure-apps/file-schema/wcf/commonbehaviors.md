---
title: <commonBehaviors>
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: 73bf759fd3dfa87398aa74de93160a4ffce08eba
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "61704356"
---
# \<commonBehaviors>
<span data-ttu-id="ff4bd-101">A `commonBehaviors` seção só pode ser definida no arquivo Machine. config.</span><span class="sxs-lookup"><span data-stu-id="ff4bd-101">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="ff4bd-102">Ele define duas coleções filho chamadas `endpointBehaviors` e `serviceBehaviors` .</span><span class="sxs-lookup"><span data-stu-id="ff4bd-102">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="ff4bd-103">Cada coleção define elementos de comportamento consumidos por todos os pontos de extremidade do WCF e serviços no computador, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="ff4bd-103">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span> <span data-ttu-id="ff4bd-104">Os comportamentos definidos em `endpointBehaviors` são aplicados somente aos clientes, e os comportamentos definidos no `serviceBehaviors` são aplicados somente aos serviços.</span><span class="sxs-lookup"><span data-stu-id="ff4bd-104">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="ff4bd-105">Se um comportamento for definido em ambas `commonBehaviors` as `behaviors` seções e, o comportamento na `behaviors` seção terá preferência.</span><span class="sxs-lookup"><span data-stu-id="ff4bd-105">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
