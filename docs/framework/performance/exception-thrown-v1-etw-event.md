---
title: Evento ETW Exception Thrown_V1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 60013d0df8c63033f6da8d61479bacac7b944094
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="exception-thrownv1-etw-event"></a><span data-ttu-id="0d222-102">Evento ETW Exception Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="0d222-102">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="0d222-103">Esse evento captura informações sobre as exceções geradas.</span><span class="sxs-lookup"><span data-stu-id="0d222-103">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="0d222-104">A tabela a seguir mostra a palavra-chave com a qual o evento é acionado, além do nível do evento.</span><span class="sxs-lookup"><span data-stu-id="0d222-104">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="0d222-105">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="0d222-105">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="0d222-106">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="0d222-106">Keyword for raising the event</span></span>|<span data-ttu-id="0d222-107">Nível</span><span class="sxs-lookup"><span data-stu-id="0d222-107">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="0d222-108">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="0d222-108">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="0d222-109">Aviso (2)</span><span class="sxs-lookup"><span data-stu-id="0d222-109">Warning (2)</span></span>|  
  
 <span data-ttu-id="0d222-110">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="0d222-110">The following table shows event information.</span></span>  
  
|<span data-ttu-id="0d222-111">evento</span><span class="sxs-lookup"><span data-stu-id="0d222-111">Event</span></span>|<span data-ttu-id="0d222-112">ID do evento</span><span class="sxs-lookup"><span data-stu-id="0d222-112">Event ID</span></span>|<span data-ttu-id="0d222-113">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="0d222-113">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="0d222-114">80</span><span class="sxs-lookup"><span data-stu-id="0d222-114">80</span></span>|<span data-ttu-id="0d222-115">Uma exceção gerenciada é gerada.</span><span class="sxs-lookup"><span data-stu-id="0d222-115">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="0d222-116">A tabela a seguir mostra dados do evento.</span><span class="sxs-lookup"><span data-stu-id="0d222-116">The following table shows event data.</span></span>  
  
|<span data-ttu-id="0d222-117">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="0d222-117">Field name</span></span>|<span data-ttu-id="0d222-118">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="0d222-118">Data type</span></span>|<span data-ttu-id="0d222-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d222-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0d222-120">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="0d222-120">Exception Type</span></span>|<span data-ttu-id="0d222-121">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="0d222-121">win:UnicodeString</span></span>|<span data-ttu-id="0d222-122">Tipo da exceção; por exemplo, `System.NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="0d222-122">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="0d222-123">Mensagem de exceção</span><span class="sxs-lookup"><span data-stu-id="0d222-123">Exception Message</span></span>|<span data-ttu-id="0d222-124">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="0d222-124">win:UnicodeString</span></span>|<span data-ttu-id="0d222-125">A mensagem de exceção real.</span><span class="sxs-lookup"><span data-stu-id="0d222-125">Actual exception message.</span></span>|  
|<span data-ttu-id="0d222-126">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="0d222-126">EIPCodeThrow</span></span>|<span data-ttu-id="0d222-127">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="0d222-127">win:Pointer</span></span>|<span data-ttu-id="0d222-128">Ponteiro de instrução em que ocorreu a exceção.</span><span class="sxs-lookup"><span data-stu-id="0d222-128">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="0d222-129">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="0d222-129">ExceptionHR</span></span>|<span data-ttu-id="0d222-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0d222-130">win:UInt32</span></span>|<span data-ttu-id="0d222-131">Exceção [HRESULT](http://go.microsoft.com/fwlink/?LinkId=179679).</span><span class="sxs-lookup"><span data-stu-id="0d222-131">Exception [HRESULT](http://go.microsoft.com/fwlink/?LinkId=179679).</span></span>|  
|<span data-ttu-id="0d222-132">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="0d222-132">ExceptionFlags</span></span>|<span data-ttu-id="0d222-133">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0d222-133">win:UInt16</span></span>|<span data-ttu-id="0d222-134">0x01: HasInnerException (consulte [Eventos CLR ETW](../../../docs/framework/performance/clr-etw-events.md) na documentação do Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="0d222-134">0x01: HasInnerException (see [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="0d222-135">0x02: IsNestedException.</span><span class="sxs-lookup"><span data-stu-id="0d222-135">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="0d222-136">0x04: IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="0d222-136">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="0d222-137">0x08: IsCorruptedStateException (indica que o estado do processo está corrompido; consulte [Tratando exceções de estado corrompido](http://go.microsoft.com/fwlink/?LinkId=179681) no MSDN).</span><span class="sxs-lookup"><span data-stu-id="0d222-137">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](http://go.microsoft.com/fwlink/?LinkId=179681) on MSDN).</span></span><br /><br /> <span data-ttu-id="0d222-138">0x10: IsCLSCompliant (uma exceção que é derivada de <xref:System.Exception> está em conformidade com CLS; caso contrário, ela não está em conformidade com CLS).</span><span class="sxs-lookup"><span data-stu-id="0d222-138">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="0d222-139">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0d222-139">ClrInstanceID</span></span>|<span data-ttu-id="0d222-140">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0d222-140">win:UInt16</span></span>|<span data-ttu-id="0d222-141">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0d222-141">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0d222-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d222-142">See Also</span></span>  
 [<span data-ttu-id="0d222-143">Eventos de CLR ETW</span><span class="sxs-lookup"><span data-stu-id="0d222-143">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
