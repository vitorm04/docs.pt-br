---
title: Evento ETW de pilha
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b0cb166f2753b910465aabb8abd68c31c6f56ff8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497532"
---
# <a name="stack-etw-event"></a><span data-ttu-id="f78a1-102">Evento ETW de pilha</span><span class="sxs-lookup"><span data-stu-id="f78a1-102">Stack ETW Event</span></span>
<span data-ttu-id="f78a1-103">O evento de pilha deve ser usado em conjunto com outros eventos para gerar rastreamentos de pilha depois que um evento é acionado.</span><span class="sxs-lookup"><span data-stu-id="f78a1-103">The stack event should be used in conjunction with other events to generate stack traces after an event is raised.</span></span> <span data-ttu-id="f78a1-104">Ele é registrado quando o provedor de tempo de execução está habilitado.</span><span class="sxs-lookup"><span data-stu-id="f78a1-104">It is logged when the runtime provider is enabled.</span></span> <span data-ttu-id="f78a1-105">Esse é um evento de alta frequência porque é acionado sempre que outro evento de tempo de execução é acionado.</span><span class="sxs-lookup"><span data-stu-id="f78a1-105">This is a very high frequency event, because it is raised whenever another runtime event is raised.</span></span> <span data-ttu-id="f78a1-106">Por esse motivo, recomendamos ter cautela ao usar esse evento.</span><span class="sxs-lookup"><span data-stu-id="f78a1-106">For this reason, we recommend that you use this event with caution.</span></span>  
  
 <span data-ttu-id="f78a1-107">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="f78a1-107">The following table shows the keyword and level.</span></span> <span data-ttu-id="f78a1-108">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="f78a1-108">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="f78a1-109">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="f78a1-109">Keyword for raising the event</span></span>|<span data-ttu-id="f78a1-110">Nível</span><span class="sxs-lookup"><span data-stu-id="f78a1-110">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f78a1-111">`StackKeyword` (0x40000000)</span><span class="sxs-lookup"><span data-stu-id="f78a1-111">`StackKeyword` (0x40000000)</span></span>|<span data-ttu-id="f78a1-112">LogAlways(0)</span><span class="sxs-lookup"><span data-stu-id="f78a1-112">LogAlways(0)</span></span>|  
  
 <span data-ttu-id="f78a1-113">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="f78a1-113">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f78a1-114">evento</span><span class="sxs-lookup"><span data-stu-id="f78a1-114">Event</span></span>|<span data-ttu-id="f78a1-115">ID do evento</span><span class="sxs-lookup"><span data-stu-id="f78a1-115">Event ID</span></span>|<span data-ttu-id="f78a1-116">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="f78a1-116">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|<span data-ttu-id="f78a1-117">82</span><span class="sxs-lookup"><span data-stu-id="f78a1-117">82</span></span>|<span data-ttu-id="f78a1-118">Em conjunto com outros eventos para gerar rastreamentos de pilha após um evento.</span><span class="sxs-lookup"><span data-stu-id="f78a1-118">In conjunction with other events to generate stack traces following an event.</span></span>|  
  
 <span data-ttu-id="f78a1-119">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="f78a1-119">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f78a1-120">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="f78a1-120">Field name</span></span>|<span data-ttu-id="f78a1-121">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="f78a1-121">Data Type</span></span>|<span data-ttu-id="f78a1-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="f78a1-122">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f78a1-123">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f78a1-123">ClrInstanceID</span></span>|<span data-ttu-id="f78a1-124">win:Uint16</span><span class="sxs-lookup"><span data-stu-id="f78a1-124">win:Uint16</span></span>|<span data-ttu-id="f78a1-125">Identificador exclusivo do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f78a1-125">Unique runtime identifier.</span></span>|  
|<span data-ttu-id="f78a1-126">Reserved1</span><span class="sxs-lookup"><span data-stu-id="f78a1-126">Reserved1</span></span>|<span data-ttu-id="f78a1-127">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="f78a1-127">win:UInt8</span></span>|<span data-ttu-id="f78a1-128">Reservado.</span><span class="sxs-lookup"><span data-stu-id="f78a1-128">Reserved.</span></span>|  
|<span data-ttu-id="f78a1-129">Reserved2</span><span class="sxs-lookup"><span data-stu-id="f78a1-129">Reserved2</span></span>|<span data-ttu-id="f78a1-130">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="f78a1-130">win:UInt8</span></span>|<span data-ttu-id="f78a1-131">Reservado.</span><span class="sxs-lookup"><span data-stu-id="f78a1-131">Reserved.</span></span>|  
|<span data-ttu-id="f78a1-132">FrameCount</span><span class="sxs-lookup"><span data-stu-id="f78a1-132">FrameCount</span></span>|<span data-ttu-id="f78a1-133">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f78a1-133">win:UInt32</span></span>|<span data-ttu-id="f78a1-134">O número de quadros no rastreamento de pilha.</span><span class="sxs-lookup"><span data-stu-id="f78a1-134">The number of frames in the stack trace.</span></span>|  
|<span data-ttu-id="f78a1-135">Pilha</span><span class="sxs-lookup"><span data-stu-id="f78a1-135">Stack</span></span>|<span data-ttu-id="f78a1-136">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="f78a1-136">win:Pointer</span></span>|<span data-ttu-id="f78a1-137">Colunas de ponteiros de instrução.</span><span class="sxs-lookup"><span data-stu-id="f78a1-137">Columns of instruction pointers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f78a1-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f78a1-138">See also</span></span>
- [<span data-ttu-id="f78a1-139">Eventos de CLR ETW</span><span class="sxs-lookup"><span data-stu-id="f78a1-139">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
