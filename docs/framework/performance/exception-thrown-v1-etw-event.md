---
title: Evento ETW Exception Thrown_V1
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dd322d25d91bb277a4c817594c968c28a6d61d68
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723011"
---
# <a name="exception-thrownv1-etw-event"></a><span data-ttu-id="18055-102">Evento ETW Exception Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="18055-102">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="18055-103">Esse evento captura informações sobre as exceções geradas.</span><span class="sxs-lookup"><span data-stu-id="18055-103">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="18055-104">A tabela a seguir mostra a palavra-chave com a qual o evento é acionado, além do nível do evento.</span><span class="sxs-lookup"><span data-stu-id="18055-104">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="18055-105">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="18055-105">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="18055-106">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="18055-106">Keyword for raising the event</span></span>|<span data-ttu-id="18055-107">Nível</span><span class="sxs-lookup"><span data-stu-id="18055-107">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="18055-108">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="18055-108">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="18055-109">Aviso (2)</span><span class="sxs-lookup"><span data-stu-id="18055-109">Warning (2)</span></span>|  
  
 <span data-ttu-id="18055-110">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="18055-110">The following table shows event information.</span></span>  
  
|<span data-ttu-id="18055-111">evento</span><span class="sxs-lookup"><span data-stu-id="18055-111">Event</span></span>|<span data-ttu-id="18055-112">ID do evento</span><span class="sxs-lookup"><span data-stu-id="18055-112">Event ID</span></span>|<span data-ttu-id="18055-113">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="18055-113">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="18055-114">80</span><span class="sxs-lookup"><span data-stu-id="18055-114">80</span></span>|<span data-ttu-id="18055-115">Uma exceção gerenciada é gerada.</span><span class="sxs-lookup"><span data-stu-id="18055-115">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="18055-116">A tabela a seguir mostra dados do evento.</span><span class="sxs-lookup"><span data-stu-id="18055-116">The following table shows event data.</span></span>  
  
|<span data-ttu-id="18055-117">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="18055-117">Field name</span></span>|<span data-ttu-id="18055-118">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="18055-118">Data type</span></span>|<span data-ttu-id="18055-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="18055-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="18055-120">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="18055-120">Exception Type</span></span>|<span data-ttu-id="18055-121">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="18055-121">win:UnicodeString</span></span>|<span data-ttu-id="18055-122">Tipo da exceção; por exemplo, `System.NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="18055-122">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="18055-123">Mensagem de exceção</span><span class="sxs-lookup"><span data-stu-id="18055-123">Exception Message</span></span>|<span data-ttu-id="18055-124">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="18055-124">win:UnicodeString</span></span>|<span data-ttu-id="18055-125">A mensagem de exceção real.</span><span class="sxs-lookup"><span data-stu-id="18055-125">Actual exception message.</span></span>|  
|<span data-ttu-id="18055-126">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="18055-126">EIPCodeThrow</span></span>|<span data-ttu-id="18055-127">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="18055-127">win:Pointer</span></span>|<span data-ttu-id="18055-128">Ponteiro de instrução em que ocorreu a exceção.</span><span class="sxs-lookup"><span data-stu-id="18055-128">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="18055-129">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="18055-129">ExceptionHR</span></span>|<span data-ttu-id="18055-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="18055-130">win:UInt32</span></span>|<span data-ttu-id="18055-131">Exceção [HRESULT](https://go.microsoft.com/fwlink/?LinkId=179679).</span><span class="sxs-lookup"><span data-stu-id="18055-131">Exception [HRESULT](https://go.microsoft.com/fwlink/?LinkId=179679).</span></span>|  
|<span data-ttu-id="18055-132">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="18055-132">ExceptionFlags</span></span>|<span data-ttu-id="18055-133">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="18055-133">win:UInt16</span></span>|<span data-ttu-id="18055-134">0x01: HasInnerException (consulte [eventos CLR ETW](../../../docs/framework/performance/clr-etw-events.md) na documentação do Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="18055-134">0x01: HasInnerException (see [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="18055-135">0x02: IsNestedException.</span><span class="sxs-lookup"><span data-stu-id="18055-135">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="18055-136">0x04: IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="18055-136">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="18055-137">0x08: IsCorruptedStateException (indica que o estado do processo está corrompido; consulte [tratamento de exceções de estado corrompido](https://go.microsoft.com/fwlink/?LinkId=179681) no MSDN).</span><span class="sxs-lookup"><span data-stu-id="18055-137">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](https://go.microsoft.com/fwlink/?LinkId=179681) on MSDN).</span></span><br /><br /> <span data-ttu-id="18055-138">0x10: IsCLSCompliant (uma exceção que é derivada de <xref:System.Exception> é compatível com CLS; caso contrário, ele não é compatível com CLS).</span><span class="sxs-lookup"><span data-stu-id="18055-138">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="18055-139">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="18055-139">ClrInstanceID</span></span>|<span data-ttu-id="18055-140">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="18055-140">win:UInt16</span></span>|<span data-ttu-id="18055-141">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="18055-141">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="18055-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="18055-142">See also</span></span>

- [<span data-ttu-id="18055-143">Eventos de CLR ETW</span><span class="sxs-lookup"><span data-stu-id="18055-143">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
