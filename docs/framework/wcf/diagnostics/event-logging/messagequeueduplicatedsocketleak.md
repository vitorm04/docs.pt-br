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
ms.workload: dotnet
ms.openlocfilehash: 3ea58a826920d440ab903270f796a3d94d17ad47
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="messagequeueduplicatedsocketleak"></a><span data-ttu-id="b24ba-102">MessageQueueDuplicatedSocketLeak</span><span class="sxs-lookup"><span data-stu-id="b24ba-102">MessageQueueDuplicatedSocketLeak</span></span>
<span data-ttu-id="b24ba-103">ID: 165</span><span class="sxs-lookup"><span data-stu-id="b24ba-103">Id: 165</span></span>  
  
 <span data-ttu-id="b24ba-104">Severidade: erro</span><span class="sxs-lookup"><span data-stu-id="b24ba-104">Severity: Error</span></span>  
  
 <span data-ttu-id="b24ba-105">Categoria: SMSvcHost</span><span class="sxs-lookup"><span data-stu-id="b24ba-105">Category: SMSvcHost</span></span>  
  
## <a name="description"></a><span data-ttu-id="b24ba-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="b24ba-106">Description</span></span>  
 <span data-ttu-id="b24ba-107">Esse evento indica que ocorreu um erro durante o envio de um soquete duplicado.</span><span class="sxs-lookup"><span data-stu-id="b24ba-107">This event indicates that an error occurred while dispatching a duplicated socket.</span></span> <span data-ttu-id="b24ba-108">Essa alça agora está perdida no processo.</span><span class="sxs-lookup"><span data-stu-id="b24ba-108">This handle is now leaked in the process.</span></span> <span data-ttu-id="b24ba-109">O evento de lista de origem, exceção, o nome do processo e ID de processo.</span><span class="sxs-lookup"><span data-stu-id="b24ba-109">The event lists the Source, Exception, Process Name and Process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b24ba-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b24ba-110">See Also</span></span>  
 [<span data-ttu-id="b24ba-111">Registro de eventos em log</span><span class="sxs-lookup"><span data-stu-id="b24ba-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="b24ba-112">Referência geral de eventos</span><span class="sxs-lookup"><span data-stu-id="b24ba-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
