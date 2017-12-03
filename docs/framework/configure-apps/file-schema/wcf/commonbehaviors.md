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
ms.openlocfilehash: 06d09763b0281eb7edafadbbd59ff924b751d73e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltcommonbehaviorsgt"></a><span data-ttu-id="eefcc-102">&lt;commonBehaviors&gt;</span><span class="sxs-lookup"><span data-stu-id="eefcc-102">&lt;commonBehaviors&gt;</span></span>
<span data-ttu-id="eefcc-103">O `commonBehaviors` seção só pode ser definida no arquivo Machine. config.</span><span class="sxs-lookup"><span data-stu-id="eefcc-103">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="eefcc-104">Ele define duas coleções filhas nomeadas `endpointBehaviors` e `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="eefcc-104">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="eefcc-105">Cada coleção define elementos de comportamento consumidos por todos os [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] pontos de extremidade e serviços no computador respectivamente.</span><span class="sxs-lookup"><span data-stu-id="eefcc-105">Each collection defines behavior elements consumed by all [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] endpoints and services on the machine respectively.</span></span> <span data-ttu-id="eefcc-106">Comportamentos definidos no `endpointBehaviors` são aplicadas apenas a clientes e comportamentos definidos no `serviceBehaviors` são aplicadas apenas a serviços.</span><span class="sxs-lookup"><span data-stu-id="eefcc-106">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="eefcc-107">Se um comportamento é definido em `commonBehaviors` e `behaviors` seções, o comportamento de `behaviors` seção tem preferência.</span><span class="sxs-lookup"><span data-stu-id="eefcc-107">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
