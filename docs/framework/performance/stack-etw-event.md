---
title: Evento ETW de pilha
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 55219fe755f49b6edbd3b53cc686bf4f9087aa08
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="stack-etw-event"></a><span data-ttu-id="f8399-102">Evento ETW de pilha</span><span class="sxs-lookup"><span data-stu-id="f8399-102">Stack ETW Event</span></span>
<span data-ttu-id="f8399-103">O evento de pilha deve ser usado em conjunto com outros eventos para gerar rastreamentos de pilha depois que um evento é acionado.</span><span class="sxs-lookup"><span data-stu-id="f8399-103">The stack event should be used in conjunction with other events to generate stack traces after an event is raised.</span></span> <span data-ttu-id="f8399-104">Ele é registrado quando o provedor de tempo de execução está habilitado.</span><span class="sxs-lookup"><span data-stu-id="f8399-104">It is logged when the runtime provider is enabled.</span></span> <span data-ttu-id="f8399-105">Esse é um evento de alta frequência porque é acionado sempre que outro evento de tempo de execução é acionado.</span><span class="sxs-lookup"><span data-stu-id="f8399-105">This is a very high frequency event, because it is raised whenever another runtime event is raised.</span></span> <span data-ttu-id="f8399-106">Por esse motivo, recomendamos ter cautela ao usar esse evento.</span><span class="sxs-lookup"><span data-stu-id="f8399-106">For this reason, we recommend that you use this event with caution.</span></span>  
  
 <span data-ttu-id="f8399-107">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="f8399-107">The following table shows the keyword and level.</span></span> <span data-ttu-id="f8399-108">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="f8399-108">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="f8399-109">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="f8399-109">Keyword for raising the event</span></span>|<span data-ttu-id="f8399-110">Nível</span><span class="sxs-lookup"><span data-stu-id="f8399-110">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f8399-111">`StackKeyword` (0x40000000)</span><span class="sxs-lookup"><span data-stu-id="f8399-111">`StackKeyword` (0x40000000)</span></span>|<span data-ttu-id="f8399-112">LogAlways(0)</span><span class="sxs-lookup"><span data-stu-id="f8399-112">LogAlways(0)</span></span>|  
  
 <span data-ttu-id="f8399-113">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="f8399-113">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f8399-114">Evento</span><span class="sxs-lookup"><span data-stu-id="f8399-114">Event</span></span>|<span data-ttu-id="f8399-115">ID do evento</span><span class="sxs-lookup"><span data-stu-id="f8399-115">Event ID</span></span>|<span data-ttu-id="f8399-116">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="f8399-116">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|<span data-ttu-id="f8399-117">82</span><span class="sxs-lookup"><span data-stu-id="f8399-117">82</span></span>|<span data-ttu-id="f8399-118">Em conjunto com outros eventos para gerar rastreamentos de pilha após um evento.</span><span class="sxs-lookup"><span data-stu-id="f8399-118">In conjunction with other events to generate stack traces following an event.</span></span>|  
  
 <span data-ttu-id="f8399-119">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="f8399-119">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f8399-120">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="f8399-120">Field name</span></span>|<span data-ttu-id="f8399-121">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="f8399-121">Data Type</span></span>|<span data-ttu-id="f8399-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="f8399-122">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f8399-123">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f8399-123">ClrInstanceID</span></span>|<span data-ttu-id="f8399-124">win:Uint16</span><span class="sxs-lookup"><span data-stu-id="f8399-124">win:Uint16</span></span>|<span data-ttu-id="f8399-125">Identificador exclusivo do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f8399-125">Unique runtime identifier.</span></span>|  
|<span data-ttu-id="f8399-126">Reserved1</span><span class="sxs-lookup"><span data-stu-id="f8399-126">Reserved1</span></span>|<span data-ttu-id="f8399-127">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="f8399-127">win:UInt8</span></span>|<span data-ttu-id="f8399-128">Reservado.</span><span class="sxs-lookup"><span data-stu-id="f8399-128">Reserved.</span></span>|  
|<span data-ttu-id="f8399-129">Reserved2</span><span class="sxs-lookup"><span data-stu-id="f8399-129">Reserved2</span></span>|<span data-ttu-id="f8399-130">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="f8399-130">win:UInt8</span></span>|<span data-ttu-id="f8399-131">Reservado.</span><span class="sxs-lookup"><span data-stu-id="f8399-131">Reserved.</span></span>|  
|<span data-ttu-id="f8399-132">FrameCount</span><span class="sxs-lookup"><span data-stu-id="f8399-132">FrameCount</span></span>|<span data-ttu-id="f8399-133">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f8399-133">win:UInt32</span></span>|<span data-ttu-id="f8399-134">O número de quadros no rastreamento de pilha.</span><span class="sxs-lookup"><span data-stu-id="f8399-134">The number of frames in the stack trace.</span></span>|  
|<span data-ttu-id="f8399-135">Pilha</span><span class="sxs-lookup"><span data-stu-id="f8399-135">Stack</span></span>|<span data-ttu-id="f8399-136">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="f8399-136">win:Pointer</span></span>|<span data-ttu-id="f8399-137">Colunas de ponteiros de instrução.</span><span class="sxs-lookup"><span data-stu-id="f8399-137">Columns of instruction pointers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f8399-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f8399-138">See Also</span></span>  
 [<span data-ttu-id="f8399-139">Eventos de CLR ETW</span><span class="sxs-lookup"><span data-stu-id="f8399-139">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
