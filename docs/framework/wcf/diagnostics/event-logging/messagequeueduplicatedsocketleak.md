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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 374a5900839dc1f0151743126de16369fa6bf7ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="messagequeueduplicatedsocketleak"></a><span data-ttu-id="b3bf5-102">MessageQueueDuplicatedSocketLeak</span><span class="sxs-lookup"><span data-stu-id="b3bf5-102">MessageQueueDuplicatedSocketLeak</span></span>
<span data-ttu-id="b3bf5-103">ID: 165</span><span class="sxs-lookup"><span data-stu-id="b3bf5-103">Id: 165</span></span>  
  
 <span data-ttu-id="b3bf5-104">Severidade: erro</span><span class="sxs-lookup"><span data-stu-id="b3bf5-104">Severity: Error</span></span>  
  
 <span data-ttu-id="b3bf5-105">Categoria: SMSvcHost</span><span class="sxs-lookup"><span data-stu-id="b3bf5-105">Category: SMSvcHost</span></span>  
  
## <a name="description"></a><span data-ttu-id="b3bf5-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="b3bf5-106">Description</span></span>  
 <span data-ttu-id="b3bf5-107">Esse evento indica que ocorreu um erro durante o envio de um soquete duplicado.</span><span class="sxs-lookup"><span data-stu-id="b3bf5-107">This event indicates that an error occurred while dispatching a duplicated socket.</span></span> <span data-ttu-id="b3bf5-108">Essa alça agora está perdida no processo.</span><span class="sxs-lookup"><span data-stu-id="b3bf5-108">This handle is now leaked in the process.</span></span> <span data-ttu-id="b3bf5-109">O evento de lista de origem, exceção, o nome do processo e ID de processo.</span><span class="sxs-lookup"><span data-stu-id="b3bf5-109">The event lists the Source, Exception, Process Name and Process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3bf5-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3bf5-110">See Also</span></span>  
 [<span data-ttu-id="b3bf5-111">Log de eventos</span><span class="sxs-lookup"><span data-stu-id="b3bf5-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="b3bf5-112">Referência geral de eventos</span><span class="sxs-lookup"><span data-stu-id="b3bf5-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
