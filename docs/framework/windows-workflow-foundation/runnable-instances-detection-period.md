---
title: "Período viável de detecção de instâncias"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ea5c787-b638-47fd-bfc8-ede8c2898ce6
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 18b016cdf51ec95ab8457ded2949b980fc66fad0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="runnable-instances-detection-period"></a><span data-ttu-id="76c81-102">Período viável de detecção de instâncias</span><span class="sxs-lookup"><span data-stu-id="76c81-102">Runnable Instances Detection Period</span></span>
<span data-ttu-id="76c81-103">A instância Store de fluxo de trabalho do SQL executa uma tarefa periodicamente interna que acorde e detecte instâncias praticáveis ou activatable na base de dados de persistência.</span><span class="sxs-lookup"><span data-stu-id="76c81-103">The SQL Workflow Instance Store runs an internal task that periodically wakes up and detects runnable or activatable instances in the persistence database.</span></span> <span data-ttu-id="76c81-104">O **período de detecção de instâncias executáveis** propriedade do repositório de instância de fluxo de trabalho SQL Especifica o período de tempo após o qual o armazenamento de instância de fluxo de trabalho do SQL executa uma tarefa de detecção para detectar qualquer fluxo de trabalho ativável ou executável instâncias do banco de dados de persistência após o ciclo de detecção anterior.</span><span class="sxs-lookup"><span data-stu-id="76c81-104">The **Runnable Instances Detection Period** property of the SQL Workflow Instance Store specifies the time period after which the SQL Workflow Instance Store runs a detection task to detect any runnable or activatable workflow instances in the persistence database after the previous detection cycle.</span></span>  
  
 <span data-ttu-id="76c81-105">Definir um intervalo menor para essa propriedade reduz o tempo entre a validade de um timer associado com uma instância de fluxo de trabalho e a sinalização de evento e de carregamento de instância subsequente.</span><span class="sxs-lookup"><span data-stu-id="76c81-105">Setting a shorter interval for this property reduces the time between the expiration of a timer associated with a workflow instance and the signaling of the event and subsequent loading of the instance.</span></span> <span data-ttu-id="76c81-106">No entanto, também aumenta a carga de processamento em um host e não pode ser desejável em situações onde timers e/ou falhas duráveis host são incomuns.</span><span class="sxs-lookup"><span data-stu-id="76c81-106">However, it also increases the processing load on a host and may not be desirable in scenarios where durable timers and/or host failures are rare.</span></span> <span data-ttu-id="76c81-107">O tipo de propriedade é período e o valor da propriedade segue o formato: hh:mm:ss.</span><span class="sxs-lookup"><span data-stu-id="76c81-107">The type of the property is TimeSpan and the value of the property follows the format: hh:mm:ss.</span></span> <span data-ttu-id="76c81-108">O valor mínimo para essa propriedade é 00:00:01.</span><span class="sxs-lookup"><span data-stu-id="76c81-108">The minimum value for this property is 00:00:01.</span></span> <span data-ttu-id="76c81-109">O valor padrão para a propriedade é 00:00:05.</span><span class="sxs-lookup"><span data-stu-id="76c81-109">The default value for the property is 00:00:05.</span></span>  
  
 <span data-ttu-id="76c81-110">Para obter mais informações consulte detectando e ativar instâncias de fluxo de trabalho executável e ativável [ativação de instância](../../../docs/framework/windows-workflow-foundation/instance-activation.md).</span><span class="sxs-lookup"><span data-stu-id="76c81-110">For more information detecting and activating runnable and activatable workflow instances, see [Instance Activation](../../../docs/framework/windows-workflow-foundation/instance-activation.md).</span></span>
