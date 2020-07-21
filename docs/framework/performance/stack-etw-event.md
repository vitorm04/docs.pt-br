---
title: Evento ETW de pilha
description: Leia sobre o evento ETW de pilha, que deve ser usado em conjunto com outros eventos para gerar rastreamentos de pilha depois que um evento é gerado.
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
ms.openlocfilehash: cab496615c4ef17831895b72c8987917e3c06e77
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474131"
---
# <a name="stack-etw-event"></a><span data-ttu-id="ef19e-103">Evento ETW de pilha</span><span class="sxs-lookup"><span data-stu-id="ef19e-103">Stack ETW Event</span></span>
<span data-ttu-id="ef19e-104">O evento de pilha deve ser usado em conjunto com outros eventos para gerar rastreamentos de pilha depois que um evento é acionado.</span><span class="sxs-lookup"><span data-stu-id="ef19e-104">The stack event should be used in conjunction with other events to generate stack traces after an event is raised.</span></span> <span data-ttu-id="ef19e-105">Ele é registrado quando o provedor de runtime está habilitado.</span><span class="sxs-lookup"><span data-stu-id="ef19e-105">It is logged when the runtime provider is enabled.</span></span> <span data-ttu-id="ef19e-106">Esse é um evento de alta frequência porque é acionado sempre que outro evento de runtime é acionado.</span><span class="sxs-lookup"><span data-stu-id="ef19e-106">This is a very high frequency event, because it is raised whenever another runtime event is raised.</span></span> <span data-ttu-id="ef19e-107">Por esse motivo, recomendamos ter cautela ao usar esse evento.</span><span class="sxs-lookup"><span data-stu-id="ef19e-107">For this reason, we recommend that you use this event with caution.</span></span>  
  
 <span data-ttu-id="ef19e-108">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="ef19e-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="ef19e-109">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="ef19e-109">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="ef19e-110">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="ef19e-110">Keyword for raising the event</span></span>|<span data-ttu-id="ef19e-111">Nível</span><span class="sxs-lookup"><span data-stu-id="ef19e-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="ef19e-112">`StackKeyword` (0x40000000)</span><span class="sxs-lookup"><span data-stu-id="ef19e-112">`StackKeyword` (0x40000000)</span></span>|<span data-ttu-id="ef19e-113">LogAlways(0)</span><span class="sxs-lookup"><span data-stu-id="ef19e-113">LogAlways(0)</span></span>|  
  
 <span data-ttu-id="ef19e-114">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="ef19e-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="ef19e-115">Evento</span><span class="sxs-lookup"><span data-stu-id="ef19e-115">Event</span></span>|<span data-ttu-id="ef19e-116">ID do evento</span><span class="sxs-lookup"><span data-stu-id="ef19e-116">Event ID</span></span>|<span data-ttu-id="ef19e-117">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="ef19e-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|<span data-ttu-id="ef19e-118">82</span><span class="sxs-lookup"><span data-stu-id="ef19e-118">82</span></span>|<span data-ttu-id="ef19e-119">Em conjunto com outros eventos para gerar rastreamentos de pilha após um evento.</span><span class="sxs-lookup"><span data-stu-id="ef19e-119">In conjunction with other events to generate stack traces following an event.</span></span>|  
  
 <span data-ttu-id="ef19e-120">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="ef19e-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="ef19e-121">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="ef19e-121">Field name</span></span>|<span data-ttu-id="ef19e-122">Tipo de Dados</span><span class="sxs-lookup"><span data-stu-id="ef19e-122">Data Type</span></span>|<span data-ttu-id="ef19e-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="ef19e-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="ef19e-124">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="ef19e-124">ClrInstanceID</span></span>|<span data-ttu-id="ef19e-125">win:Uint16</span><span class="sxs-lookup"><span data-stu-id="ef19e-125">win:Uint16</span></span>|<span data-ttu-id="ef19e-126">Identificador exclusivo do runtime.</span><span class="sxs-lookup"><span data-stu-id="ef19e-126">Unique runtime identifier.</span></span>|  
|<span data-ttu-id="ef19e-127">Reserved1</span><span class="sxs-lookup"><span data-stu-id="ef19e-127">Reserved1</span></span>|<span data-ttu-id="ef19e-128">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="ef19e-128">win:UInt8</span></span>|<span data-ttu-id="ef19e-129">Reservado.</span><span class="sxs-lookup"><span data-stu-id="ef19e-129">Reserved.</span></span>|  
|<span data-ttu-id="ef19e-130">Reserved2</span><span class="sxs-lookup"><span data-stu-id="ef19e-130">Reserved2</span></span>|<span data-ttu-id="ef19e-131">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="ef19e-131">win:UInt8</span></span>|<span data-ttu-id="ef19e-132">Reservado.</span><span class="sxs-lookup"><span data-stu-id="ef19e-132">Reserved.</span></span>|  
|<span data-ttu-id="ef19e-133">FrameCount</span><span class="sxs-lookup"><span data-stu-id="ef19e-133">FrameCount</span></span>|<span data-ttu-id="ef19e-134">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="ef19e-134">win:UInt32</span></span>|<span data-ttu-id="ef19e-135">O número de quadros no rastreamento de pilha.</span><span class="sxs-lookup"><span data-stu-id="ef19e-135">The number of frames in the stack trace.</span></span>|  
|<span data-ttu-id="ef19e-136">Pilha</span><span class="sxs-lookup"><span data-stu-id="ef19e-136">Stack</span></span>|<span data-ttu-id="ef19e-137">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="ef19e-137">win:Pointer</span></span>|<span data-ttu-id="ef19e-138">Colunas de ponteiros de instrução.</span><span class="sxs-lookup"><span data-stu-id="ef19e-138">Columns of instruction pointers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ef19e-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ef19e-139">See also</span></span>

- [<span data-ttu-id="ef19e-140">Eventos ETW no CLR</span><span class="sxs-lookup"><span data-stu-id="ef19e-140">CLR ETW Events</span></span>](clr-etw-events.md)
