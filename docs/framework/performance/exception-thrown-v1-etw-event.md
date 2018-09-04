---
title: Evento ETW Exception Thrown_V1
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 865b7b16d5807bd9161855f453128a63c84eab96
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43505217"
---
# <a name="exception-thrownv1-etw-event"></a><span data-ttu-id="8d03d-102">Evento ETW Exception Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="8d03d-102">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="8d03d-103">Esse evento captura informações sobre as exceções geradas.</span><span class="sxs-lookup"><span data-stu-id="8d03d-103">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="8d03d-104">A tabela a seguir mostra a palavra-chave com a qual o evento é acionado, além do nível do evento.</span><span class="sxs-lookup"><span data-stu-id="8d03d-104">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="8d03d-105">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="8d03d-105">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="8d03d-106">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="8d03d-106">Keyword for raising the event</span></span>|<span data-ttu-id="8d03d-107">Nível</span><span class="sxs-lookup"><span data-stu-id="8d03d-107">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="8d03d-108">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="8d03d-108">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="8d03d-109">Aviso (2)</span><span class="sxs-lookup"><span data-stu-id="8d03d-109">Warning (2)</span></span>|  
  
 <span data-ttu-id="8d03d-110">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="8d03d-110">The following table shows event information.</span></span>  
  
|<span data-ttu-id="8d03d-111">evento</span><span class="sxs-lookup"><span data-stu-id="8d03d-111">Event</span></span>|<span data-ttu-id="8d03d-112">ID do evento</span><span class="sxs-lookup"><span data-stu-id="8d03d-112">Event ID</span></span>|<span data-ttu-id="8d03d-113">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="8d03d-113">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="8d03d-114">80</span><span class="sxs-lookup"><span data-stu-id="8d03d-114">80</span></span>|<span data-ttu-id="8d03d-115">Uma exceção gerenciada é gerada.</span><span class="sxs-lookup"><span data-stu-id="8d03d-115">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="8d03d-116">A tabela a seguir mostra dados do evento.</span><span class="sxs-lookup"><span data-stu-id="8d03d-116">The following table shows event data.</span></span>  
  
|<span data-ttu-id="8d03d-117">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="8d03d-117">Field name</span></span>|<span data-ttu-id="8d03d-118">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="8d03d-118">Data type</span></span>|<span data-ttu-id="8d03d-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d03d-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="8d03d-120">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="8d03d-120">Exception Type</span></span>|<span data-ttu-id="8d03d-121">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="8d03d-121">win:UnicodeString</span></span>|<span data-ttu-id="8d03d-122">Tipo da exceção; por exemplo, `System.NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="8d03d-122">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="8d03d-123">Mensagem de exceção</span><span class="sxs-lookup"><span data-stu-id="8d03d-123">Exception Message</span></span>|<span data-ttu-id="8d03d-124">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="8d03d-124">win:UnicodeString</span></span>|<span data-ttu-id="8d03d-125">A mensagem de exceção real.</span><span class="sxs-lookup"><span data-stu-id="8d03d-125">Actual exception message.</span></span>|  
|<span data-ttu-id="8d03d-126">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="8d03d-126">EIPCodeThrow</span></span>|<span data-ttu-id="8d03d-127">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="8d03d-127">win:Pointer</span></span>|<span data-ttu-id="8d03d-128">Ponteiro de instrução em que ocorreu a exceção.</span><span class="sxs-lookup"><span data-stu-id="8d03d-128">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="8d03d-129">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="8d03d-129">ExceptionHR</span></span>|<span data-ttu-id="8d03d-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="8d03d-130">win:UInt32</span></span>|<span data-ttu-id="8d03d-131">Exceção [HRESULT](https://go.microsoft.com/fwlink/?LinkId=179679).</span><span class="sxs-lookup"><span data-stu-id="8d03d-131">Exception [HRESULT](https://go.microsoft.com/fwlink/?LinkId=179679).</span></span>|  
|<span data-ttu-id="8d03d-132">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="8d03d-132">ExceptionFlags</span></span>|<span data-ttu-id="8d03d-133">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="8d03d-133">win:UInt16</span></span>|<span data-ttu-id="8d03d-134">0x01: HasInnerException (consulte [Eventos CLR ETW](../../../docs/framework/performance/clr-etw-events.md) na documentação do Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="8d03d-134">0x01: HasInnerException (see [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="8d03d-135">0x02: IsNestedException.</span><span class="sxs-lookup"><span data-stu-id="8d03d-135">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="8d03d-136">0x04: IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="8d03d-136">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="8d03d-137">0x08: IsCorruptedStateException (indica que o estado do processo está corrompido; consulte [Tratando exceções de estado corrompido](https://go.microsoft.com/fwlink/?LinkId=179681) no MSDN).</span><span class="sxs-lookup"><span data-stu-id="8d03d-137">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](https://go.microsoft.com/fwlink/?LinkId=179681) on MSDN).</span></span><br /><br /> <span data-ttu-id="8d03d-138">0x10: IsCLSCompliant (uma exceção que é derivada de <xref:System.Exception> está em conformidade com CLS; caso contrário, ela não está em conformidade com CLS).</span><span class="sxs-lookup"><span data-stu-id="8d03d-138">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="8d03d-139">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="8d03d-139">ClrInstanceID</span></span>|<span data-ttu-id="8d03d-140">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="8d03d-140">win:UInt16</span></span>|<span data-ttu-id="8d03d-141">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="8d03d-141">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8d03d-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d03d-142">See Also</span></span>  
 [<span data-ttu-id="8d03d-143">Eventos de CLR ETW</span><span class="sxs-lookup"><span data-stu-id="8d03d-143">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
