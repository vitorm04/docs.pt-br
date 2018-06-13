---
title: '&lt;commonBehaviors&gt;'
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: 0a9fab68ce240fc37d27c42d9feff969b97f93a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350316"
---
# <a name="ltcommonbehaviorsgt"></a><span data-ttu-id="39fca-102">&lt;commonBehaviors&gt;</span><span class="sxs-lookup"><span data-stu-id="39fca-102">&lt;commonBehaviors&gt;</span></span>
<span data-ttu-id="39fca-103">O `commonBehaviors` seção só pode ser definida no arquivo Machine. config.</span><span class="sxs-lookup"><span data-stu-id="39fca-103">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="39fca-104">Ele define duas coleções filhas nomeadas `endpointBehaviors` e `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="39fca-104">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="39fca-105">Cada coleção define elementos de comportamento consumidos por todos os pontos de extremidade do WCF e serviços no computador, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="39fca-105">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span> <span data-ttu-id="39fca-106">Comportamentos definidos no `endpointBehaviors` são aplicadas apenas a clientes e comportamentos definidos no `serviceBehaviors` são aplicadas apenas a serviços.</span><span class="sxs-lookup"><span data-stu-id="39fca-106">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="39fca-107">Se um comportamento é definido em `commonBehaviors` e `behaviors` seções, o comportamento de `behaviors` seção tem preferência.</span><span class="sxs-lookup"><span data-stu-id="39fca-107">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
