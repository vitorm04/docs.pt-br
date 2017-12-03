---
title: MessageQueueDuplicatedPipeLeak
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 743db7f1-32cc-4a3b-8d1a-5d1cf25e439c
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bd1b006d735c5b8bc140efe095adeb74aef387db
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="messagequeueduplicatedpipeleak"></a><span data-ttu-id="43319-102">MessageQueueDuplicatedPipeLeak</span><span class="sxs-lookup"><span data-stu-id="43319-102">MessageQueueDuplicatedPipeLeak</span></span>
<span data-ttu-id="43319-103">ID: 166</span><span class="sxs-lookup"><span data-stu-id="43319-103">Id: 166</span></span>  
  
 <span data-ttu-id="43319-104">Severidade: erro</span><span class="sxs-lookup"><span data-stu-id="43319-104">Severity: Error</span></span>  
  
 <span data-ttu-id="43319-105">Categoria: SMSvcHost</span><span class="sxs-lookup"><span data-stu-id="43319-105">Category: SMSvcHost</span></span>  
  
## <a name="description"></a><span data-ttu-id="43319-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="43319-106">Description</span></span>  
 <span data-ttu-id="43319-107">Esse evento indica que ocorreu um erro durante o envio de um pipe nomeado duplicado.</span><span class="sxs-lookup"><span data-stu-id="43319-107">This event indicates that an error occurred while dispatching a duplicated named pipe.</span></span> <span data-ttu-id="43319-108">Essa alça agora está perdida no processo.</span><span class="sxs-lookup"><span data-stu-id="43319-108">This handle is now leaked in the process.</span></span> <span data-ttu-id="43319-109">O evento lista a origem, a exceção, o nome do processo e o ID de processo.</span><span class="sxs-lookup"><span data-stu-id="43319-109">The event lists the source, exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43319-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43319-110">See Also</span></span>  
 [<span data-ttu-id="43319-111">Log de eventos</span><span class="sxs-lookup"><span data-stu-id="43319-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="43319-112">Referência geral de eventos</span><span class="sxs-lookup"><span data-stu-id="43319-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
