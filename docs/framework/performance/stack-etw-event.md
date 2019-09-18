---
title: Evento ETW de pilha
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5dc23f5105b589d5b74c9ea6b7f40b84c2b04e6a
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046162"
---
# <a name="stack-etw-event"></a><span data-ttu-id="726f6-102">Evento ETW de pilha</span><span class="sxs-lookup"><span data-stu-id="726f6-102">Stack ETW Event</span></span>
<span data-ttu-id="726f6-103">O evento de pilha deve ser usado em conjunto com outros eventos para gerar rastreamentos de pilha depois que um evento é acionado.</span><span class="sxs-lookup"><span data-stu-id="726f6-103">The stack event should be used in conjunction with other events to generate stack traces after an event is raised.</span></span> <span data-ttu-id="726f6-104">Ele é registrado quando o provedor de tempo de execução está habilitado.</span><span class="sxs-lookup"><span data-stu-id="726f6-104">It is logged when the runtime provider is enabled.</span></span> <span data-ttu-id="726f6-105">Esse é um evento de alta frequência porque é acionado sempre que outro evento de tempo de execução é acionado.</span><span class="sxs-lookup"><span data-stu-id="726f6-105">This is a very high frequency event, because it is raised whenever another runtime event is raised.</span></span> <span data-ttu-id="726f6-106">Por esse motivo, recomendamos ter cautela ao usar esse evento.</span><span class="sxs-lookup"><span data-stu-id="726f6-106">For this reason, we recommend that you use this event with caution.</span></span>  
  
 <span data-ttu-id="726f6-107">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="726f6-107">The following table shows the keyword and level.</span></span> <span data-ttu-id="726f6-108">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="726f6-108">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="726f6-109">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="726f6-109">Keyword for raising the event</span></span>|<span data-ttu-id="726f6-110">Nível</span><span class="sxs-lookup"><span data-stu-id="726f6-110">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="726f6-111">`StackKeyword` (0x40000000)</span><span class="sxs-lookup"><span data-stu-id="726f6-111">`StackKeyword` (0x40000000)</span></span>|<span data-ttu-id="726f6-112">LogAlways(0)</span><span class="sxs-lookup"><span data-stu-id="726f6-112">LogAlways(0)</span></span>|  
  
 <span data-ttu-id="726f6-113">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="726f6-113">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="726f6-114">evento</span><span class="sxs-lookup"><span data-stu-id="726f6-114">Event</span></span>|<span data-ttu-id="726f6-115">ID do evento</span><span class="sxs-lookup"><span data-stu-id="726f6-115">Event ID</span></span>|<span data-ttu-id="726f6-116">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="726f6-116">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|<span data-ttu-id="726f6-117">82</span><span class="sxs-lookup"><span data-stu-id="726f6-117">82</span></span>|<span data-ttu-id="726f6-118">Em conjunto com outros eventos para gerar rastreamentos de pilha após um evento.</span><span class="sxs-lookup"><span data-stu-id="726f6-118">In conjunction with other events to generate stack traces following an event.</span></span>|  
  
 <span data-ttu-id="726f6-119">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="726f6-119">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="726f6-120">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="726f6-120">Field name</span></span>|<span data-ttu-id="726f6-121">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="726f6-121">Data Type</span></span>|<span data-ttu-id="726f6-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="726f6-122">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="726f6-123">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="726f6-123">ClrInstanceID</span></span>|<span data-ttu-id="726f6-124">win:Uint16</span><span class="sxs-lookup"><span data-stu-id="726f6-124">win:Uint16</span></span>|<span data-ttu-id="726f6-125">Identificador exclusivo do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="726f6-125">Unique runtime identifier.</span></span>|  
|<span data-ttu-id="726f6-126">Reserved1</span><span class="sxs-lookup"><span data-stu-id="726f6-126">Reserved1</span></span>|<span data-ttu-id="726f6-127">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="726f6-127">win:UInt8</span></span>|<span data-ttu-id="726f6-128">Reservado.</span><span class="sxs-lookup"><span data-stu-id="726f6-128">Reserved.</span></span>|  
|<span data-ttu-id="726f6-129">Reserved2</span><span class="sxs-lookup"><span data-stu-id="726f6-129">Reserved2</span></span>|<span data-ttu-id="726f6-130">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="726f6-130">win:UInt8</span></span>|<span data-ttu-id="726f6-131">Reservado.</span><span class="sxs-lookup"><span data-stu-id="726f6-131">Reserved.</span></span>|  
|<span data-ttu-id="726f6-132">FrameCount</span><span class="sxs-lookup"><span data-stu-id="726f6-132">FrameCount</span></span>|<span data-ttu-id="726f6-133">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="726f6-133">win:UInt32</span></span>|<span data-ttu-id="726f6-134">O número de quadros no rastreamento de pilha.</span><span class="sxs-lookup"><span data-stu-id="726f6-134">The number of frames in the stack trace.</span></span>|  
|<span data-ttu-id="726f6-135">Pilha</span><span class="sxs-lookup"><span data-stu-id="726f6-135">Stack</span></span>|<span data-ttu-id="726f6-136">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="726f6-136">win:Pointer</span></span>|<span data-ttu-id="726f6-137">Colunas de ponteiros de instrução.</span><span class="sxs-lookup"><span data-stu-id="726f6-137">Columns of instruction pointers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="726f6-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="726f6-138">See also</span></span>

- [<span data-ttu-id="726f6-139">Eventos de CLR ETW</span><span class="sxs-lookup"><span data-stu-id="726f6-139">CLR ETW Events</span></span>](clr-etw-events.md)
