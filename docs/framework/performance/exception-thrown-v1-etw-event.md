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
ms.openlocfilehash: dcf3390821c4210ced4c43dab5a94c93802d5f9d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="exception-thrownv1-etw-event"></a><span data-ttu-id="c9893-102">Evento ETW Exception Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="c9893-102">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="c9893-103">Esse evento captura informações sobre as exceções geradas.</span><span class="sxs-lookup"><span data-stu-id="c9893-103">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="c9893-104">A tabela a seguir mostra a palavra-chave com a qual o evento é acionado, além do nível do evento.</span><span class="sxs-lookup"><span data-stu-id="c9893-104">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="c9893-105">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="c9893-105">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="c9893-106">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="c9893-106">Keyword for raising the event</span></span>|<span data-ttu-id="c9893-107">Nível</span><span class="sxs-lookup"><span data-stu-id="c9893-107">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c9893-108">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="c9893-108">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="c9893-109">Aviso (2)</span><span class="sxs-lookup"><span data-stu-id="c9893-109">Warning (2)</span></span>|  
  
 <span data-ttu-id="c9893-110">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="c9893-110">The following table shows event information.</span></span>  
  
|<span data-ttu-id="c9893-111">Evento</span><span class="sxs-lookup"><span data-stu-id="c9893-111">Event</span></span>|<span data-ttu-id="c9893-112">ID do evento</span><span class="sxs-lookup"><span data-stu-id="c9893-112">Event ID</span></span>|<span data-ttu-id="c9893-113">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="c9893-113">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="c9893-114">80</span><span class="sxs-lookup"><span data-stu-id="c9893-114">80</span></span>|<span data-ttu-id="c9893-115">Uma exceção gerenciada é gerada.</span><span class="sxs-lookup"><span data-stu-id="c9893-115">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="c9893-116">A tabela a seguir mostra dados do evento.</span><span class="sxs-lookup"><span data-stu-id="c9893-116">The following table shows event data.</span></span>  
  
|<span data-ttu-id="c9893-117">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="c9893-117">Field name</span></span>|<span data-ttu-id="c9893-118">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="c9893-118">Data type</span></span>|<span data-ttu-id="c9893-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9893-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="c9893-120">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="c9893-120">Exception Type</span></span>|<span data-ttu-id="c9893-121">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="c9893-121">win:UnicodeString</span></span>|<span data-ttu-id="c9893-122">Tipo da exceção; por exemplo, `System.NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="c9893-122">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="c9893-123">Mensagem de exceção</span><span class="sxs-lookup"><span data-stu-id="c9893-123">Exception Message</span></span>|<span data-ttu-id="c9893-124">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="c9893-124">win:UnicodeString</span></span>|<span data-ttu-id="c9893-125">A mensagem de exceção real.</span><span class="sxs-lookup"><span data-stu-id="c9893-125">Actual exception message.</span></span>|  
|<span data-ttu-id="c9893-126">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="c9893-126">EIPCodeThrow</span></span>|<span data-ttu-id="c9893-127">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="c9893-127">win:Pointer</span></span>|<span data-ttu-id="c9893-128">Ponteiro de instrução em que ocorreu a exceção.</span><span class="sxs-lookup"><span data-stu-id="c9893-128">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="c9893-129">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="c9893-129">ExceptionHR</span></span>|<span data-ttu-id="c9893-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c9893-130">win:UInt32</span></span>|<span data-ttu-id="c9893-131">Exceção [HRESULT](http://go.microsoft.com/fwlink/?LinkId=179679).</span><span class="sxs-lookup"><span data-stu-id="c9893-131">Exception [HRESULT](http://go.microsoft.com/fwlink/?LinkId=179679).</span></span>|  
|<span data-ttu-id="c9893-132">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="c9893-132">ExceptionFlags</span></span>|<span data-ttu-id="c9893-133">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c9893-133">win:UInt16</span></span>|<span data-ttu-id="c9893-134">0x01: HasInnerException (consulte [Eventos CLR ETW](../../../docs/framework/performance/clr-etw-events.md) na documentação do Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="c9893-134">0x01: HasInnerException (see [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="c9893-135">0x02: IsNestedException.</span><span class="sxs-lookup"><span data-stu-id="c9893-135">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="c9893-136">0x04: IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="c9893-136">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="c9893-137">0x08: IsCorruptedStateException (indica que o estado do processo está corrompido; consulte [Tratando exceções de estado corrompido](http://go.microsoft.com/fwlink/?LinkId=179681) no MSDN).</span><span class="sxs-lookup"><span data-stu-id="c9893-137">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](http://go.microsoft.com/fwlink/?LinkId=179681) on MSDN).</span></span><br /><br /> <span data-ttu-id="c9893-138">0x10: IsCLSCompliant (uma exceção que é derivada de <xref:System.Exception> está em conformidade com CLS; caso contrário, ela não está em conformidade com CLS).</span><span class="sxs-lookup"><span data-stu-id="c9893-138">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="c9893-139">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c9893-139">ClrInstanceID</span></span>|<span data-ttu-id="c9893-140">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c9893-140">win:UInt16</span></span>|<span data-ttu-id="c9893-141">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c9893-141">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c9893-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9893-142">See Also</span></span>  
 [<span data-ttu-id="c9893-143">Eventos de CLR ETW</span><span class="sxs-lookup"><span data-stu-id="c9893-143">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
