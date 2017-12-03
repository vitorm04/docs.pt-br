---
title: MessageQueueDuplicatedSocketLeak
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9721a463-15d1-43dc-8e3a-cae44448de91
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5e1356c1b6146d2c54f81a8f4221579490068f5c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="messagequeueduplicatedsocketleak"></a><span data-ttu-id="91727-102">MessageQueueDuplicatedSocketLeak</span><span class="sxs-lookup"><span data-stu-id="91727-102">MessageQueueDuplicatedSocketLeak</span></span>
<span data-ttu-id="91727-103">ID: 165</span><span class="sxs-lookup"><span data-stu-id="91727-103">Id: 165</span></span>  
  
 <span data-ttu-id="91727-104">Severidade: erro</span><span class="sxs-lookup"><span data-stu-id="91727-104">Severity: Error</span></span>  
  
 <span data-ttu-id="91727-105">Categoria: SMSvcHost</span><span class="sxs-lookup"><span data-stu-id="91727-105">Category: SMSvcHost</span></span>  
  
## <a name="description"></a><span data-ttu-id="91727-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="91727-106">Description</span></span>  
 <span data-ttu-id="91727-107">Esse evento indica que ocorreu um erro durante o envio de um soquete duplicado.</span><span class="sxs-lookup"><span data-stu-id="91727-107">This event indicates that an error occurred while dispatching a duplicated socket.</span></span> <span data-ttu-id="91727-108">Essa alça agora está perdida no processo.</span><span class="sxs-lookup"><span data-stu-id="91727-108">This handle is now leaked in the process.</span></span> <span data-ttu-id="91727-109">O evento de lista de origem, exceção, o nome do processo e ID de processo.</span><span class="sxs-lookup"><span data-stu-id="91727-109">The event lists the Source, Exception, Process Name and Process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91727-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91727-110">See Also</span></span>  
 [<span data-ttu-id="91727-111">Log de eventos</span><span class="sxs-lookup"><span data-stu-id="91727-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="91727-112">Referência geral de eventos</span><span class="sxs-lookup"><span data-stu-id="91727-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
