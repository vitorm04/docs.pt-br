---
title: Evento ETW Exception Thrown_V1
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dafa5846f779276ab81e8e30e7c7a50b9fbff853
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393849"
---
# <a name="exception-thrownv1-etw-event"></a><span data-ttu-id="cc257-102">Evento ETW Exception Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="cc257-102">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="cc257-103">Esse evento captura informações sobre as exceções geradas.</span><span class="sxs-lookup"><span data-stu-id="cc257-103">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="cc257-104">A tabela a seguir mostra a palavra-chave com a qual o evento é acionado, além do nível do evento.</span><span class="sxs-lookup"><span data-stu-id="cc257-104">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="cc257-105">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="cc257-105">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="cc257-106">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="cc257-106">Keyword for raising the event</span></span>|<span data-ttu-id="cc257-107">Nível</span><span class="sxs-lookup"><span data-stu-id="cc257-107">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="cc257-108">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="cc257-108">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="cc257-109">Aviso (2)</span><span class="sxs-lookup"><span data-stu-id="cc257-109">Warning (2)</span></span>|  
  
 <span data-ttu-id="cc257-110">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="cc257-110">The following table shows event information.</span></span>  
  
|<span data-ttu-id="cc257-111">evento</span><span class="sxs-lookup"><span data-stu-id="cc257-111">Event</span></span>|<span data-ttu-id="cc257-112">ID do evento</span><span class="sxs-lookup"><span data-stu-id="cc257-112">Event ID</span></span>|<span data-ttu-id="cc257-113">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="cc257-113">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="cc257-114">80</span><span class="sxs-lookup"><span data-stu-id="cc257-114">80</span></span>|<span data-ttu-id="cc257-115">Uma exceção gerenciada é gerada.</span><span class="sxs-lookup"><span data-stu-id="cc257-115">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="cc257-116">A tabela a seguir mostra dados do evento.</span><span class="sxs-lookup"><span data-stu-id="cc257-116">The following table shows event data.</span></span>  
  
|<span data-ttu-id="cc257-117">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="cc257-117">Field name</span></span>|<span data-ttu-id="cc257-118">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="cc257-118">Data type</span></span>|<span data-ttu-id="cc257-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="cc257-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="cc257-120">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="cc257-120">Exception Type</span></span>|<span data-ttu-id="cc257-121">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="cc257-121">win:UnicodeString</span></span>|<span data-ttu-id="cc257-122">Tipo da exceção; por exemplo, `System.NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="cc257-122">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="cc257-123">Mensagem de exceção</span><span class="sxs-lookup"><span data-stu-id="cc257-123">Exception Message</span></span>|<span data-ttu-id="cc257-124">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="cc257-124">win:UnicodeString</span></span>|<span data-ttu-id="cc257-125">A mensagem de exceção real.</span><span class="sxs-lookup"><span data-stu-id="cc257-125">Actual exception message.</span></span>|  
|<span data-ttu-id="cc257-126">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="cc257-126">EIPCodeThrow</span></span>|<span data-ttu-id="cc257-127">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="cc257-127">win:Pointer</span></span>|<span data-ttu-id="cc257-128">Ponteiro de instrução em que ocorreu a exceção.</span><span class="sxs-lookup"><span data-stu-id="cc257-128">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="cc257-129">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="cc257-129">ExceptionHR</span></span>|<span data-ttu-id="cc257-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="cc257-130">win:UInt32</span></span>|<span data-ttu-id="cc257-131">Exceção [HRESULT](http://go.microsoft.com/fwlink/?LinkId=179679).</span><span class="sxs-lookup"><span data-stu-id="cc257-131">Exception [HRESULT](http://go.microsoft.com/fwlink/?LinkId=179679).</span></span>|  
|<span data-ttu-id="cc257-132">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="cc257-132">ExceptionFlags</span></span>|<span data-ttu-id="cc257-133">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="cc257-133">win:UInt16</span></span>|<span data-ttu-id="cc257-134">0x01: HasInnerException (consulte [Eventos CLR ETW](../../../docs/framework/performance/clr-etw-events.md) na documentação do Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="cc257-134">0x01: HasInnerException (see [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="cc257-135">0x02: IsNestedException.</span><span class="sxs-lookup"><span data-stu-id="cc257-135">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="cc257-136">0x04: IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="cc257-136">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="cc257-137">0x08: IsCorruptedStateException (indica que o estado do processo está corrompido; consulte [Tratando exceções de estado corrompido](http://go.microsoft.com/fwlink/?LinkId=179681) no MSDN).</span><span class="sxs-lookup"><span data-stu-id="cc257-137">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](http://go.microsoft.com/fwlink/?LinkId=179681) on MSDN).</span></span><br /><br /> <span data-ttu-id="cc257-138">0x10: IsCLSCompliant (uma exceção que é derivada de <xref:System.Exception> está em conformidade com CLS; caso contrário, ela não está em conformidade com CLS).</span><span class="sxs-lookup"><span data-stu-id="cc257-138">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="cc257-139">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="cc257-139">ClrInstanceID</span></span>|<span data-ttu-id="cc257-140">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="cc257-140">win:UInt16</span></span>|<span data-ttu-id="cc257-141">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="cc257-141">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cc257-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc257-142">See Also</span></span>  
 [<span data-ttu-id="cc257-143">Eventos de CLR ETW</span><span class="sxs-lookup"><span data-stu-id="cc257-143">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
