---
title: Evento ETW de pilha
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a7cba2bd1dd5b83e29c7a6c192a1a7e5e2d33ecc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076463"
---
# <a name="stack-etw-event"></a><span data-ttu-id="9fe69-102">Evento ETW de pilha</span><span class="sxs-lookup"><span data-stu-id="9fe69-102">Stack ETW Event</span></span>
<span data-ttu-id="9fe69-103">O evento de pilha deve ser usado em conjunto com outros eventos para gerar rastreamentos de pilha depois que um evento é acionado.</span><span class="sxs-lookup"><span data-stu-id="9fe69-103">The stack event should be used in conjunction with other events to generate stack traces after an event is raised.</span></span> <span data-ttu-id="9fe69-104">Ele é registrado quando o provedor de tempo de execução está habilitado.</span><span class="sxs-lookup"><span data-stu-id="9fe69-104">It is logged when the runtime provider is enabled.</span></span> <span data-ttu-id="9fe69-105">Esse é um evento de alta frequência porque é acionado sempre que outro evento de tempo de execução é acionado.</span><span class="sxs-lookup"><span data-stu-id="9fe69-105">This is a very high frequency event, because it is raised whenever another runtime event is raised.</span></span> <span data-ttu-id="9fe69-106">Por esse motivo, recomendamos ter cautela ao usar esse evento.</span><span class="sxs-lookup"><span data-stu-id="9fe69-106">For this reason, we recommend that you use this event with caution.</span></span>  
  
 <span data-ttu-id="9fe69-107">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="9fe69-107">The following table shows the keyword and level.</span></span> <span data-ttu-id="9fe69-108">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="9fe69-108">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="9fe69-109">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="9fe69-109">Keyword for raising the event</span></span>|<span data-ttu-id="9fe69-110">Nível</span><span class="sxs-lookup"><span data-stu-id="9fe69-110">Level</span></span>|  
|-----------------------------------|-----------|  
|`StackKeyword` <span data-ttu-id="9fe69-111">(0x40000000)</span><span class="sxs-lookup"><span data-stu-id="9fe69-111">(0x40000000)</span></span>|<span data-ttu-id="9fe69-112">LogAlways(0)</span><span class="sxs-lookup"><span data-stu-id="9fe69-112">LogAlways(0)</span></span>|  
  
 <span data-ttu-id="9fe69-113">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="9fe69-113">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="9fe69-114">evento</span><span class="sxs-lookup"><span data-stu-id="9fe69-114">Event</span></span>|<span data-ttu-id="9fe69-115">ID do evento</span><span class="sxs-lookup"><span data-stu-id="9fe69-115">Event ID</span></span>|<span data-ttu-id="9fe69-116">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="9fe69-116">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|<span data-ttu-id="9fe69-117">82</span><span class="sxs-lookup"><span data-stu-id="9fe69-117">82</span></span>|<span data-ttu-id="9fe69-118">Em conjunto com outros eventos para gerar rastreamentos de pilha após um evento.</span><span class="sxs-lookup"><span data-stu-id="9fe69-118">In conjunction with other events to generate stack traces following an event.</span></span>|  
  
 <span data-ttu-id="9fe69-119">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="9fe69-119">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="9fe69-120">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="9fe69-120">Field name</span></span>|<span data-ttu-id="9fe69-121">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="9fe69-121">Data Type</span></span>|<span data-ttu-id="9fe69-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="9fe69-122">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="9fe69-123">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="9fe69-123">ClrInstanceID</span></span>|<span data-ttu-id="9fe69-124">win:Uint16</span><span class="sxs-lookup"><span data-stu-id="9fe69-124">win:Uint16</span></span>|<span data-ttu-id="9fe69-125">Identificador exclusivo do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9fe69-125">Unique runtime identifier.</span></span>|  
|<span data-ttu-id="9fe69-126">Reserved1</span><span class="sxs-lookup"><span data-stu-id="9fe69-126">Reserved1</span></span>|<span data-ttu-id="9fe69-127">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="9fe69-127">win:UInt8</span></span>|<span data-ttu-id="9fe69-128">Reservado.</span><span class="sxs-lookup"><span data-stu-id="9fe69-128">Reserved.</span></span>|  
|<span data-ttu-id="9fe69-129">Reserved2</span><span class="sxs-lookup"><span data-stu-id="9fe69-129">Reserved2</span></span>|<span data-ttu-id="9fe69-130">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="9fe69-130">win:UInt8</span></span>|<span data-ttu-id="9fe69-131">Reservado.</span><span class="sxs-lookup"><span data-stu-id="9fe69-131">Reserved.</span></span>|  
|<span data-ttu-id="9fe69-132">FrameCount</span><span class="sxs-lookup"><span data-stu-id="9fe69-132">FrameCount</span></span>|<span data-ttu-id="9fe69-133">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="9fe69-133">win:UInt32</span></span>|<span data-ttu-id="9fe69-134">O número de quadros no rastreamento de pilha.</span><span class="sxs-lookup"><span data-stu-id="9fe69-134">The number of frames in the stack trace.</span></span>|  
|<span data-ttu-id="9fe69-135">Pilha</span><span class="sxs-lookup"><span data-stu-id="9fe69-135">Stack</span></span>|<span data-ttu-id="9fe69-136">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="9fe69-136">win:Pointer</span></span>|<span data-ttu-id="9fe69-137">Colunas de ponteiros de instrução.</span><span class="sxs-lookup"><span data-stu-id="9fe69-137">Columns of instruction pointers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9fe69-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9fe69-138">See also</span></span>

- [<span data-ttu-id="9fe69-139">Eventos ETW no CLR</span><span class="sxs-lookup"><span data-stu-id="9fe69-139">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
