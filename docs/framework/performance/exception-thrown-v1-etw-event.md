---
title: Evento ETW Exception Thrown_V1
description: Exiba informações detalhadas sobre o evento ExceptionThrown_V1 ETW. Dados de evento, como nomes de campo, tipos de dados e descrições, são fornecidos para exceções geradas.
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
ms.openlocfilehash: f800a43d0ed2a82bc51a5e3a028b5fa1870df3fb
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309450"
---
# <a name="exception-thrown_v1-etw-event"></a><span data-ttu-id="82bdc-104">Evento ETW Exception Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="82bdc-104">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="82bdc-105">Esse evento captura informações sobre as exceções geradas.</span><span class="sxs-lookup"><span data-stu-id="82bdc-105">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="82bdc-106">A tabela a seguir mostra a palavra-chave com a qual o evento é acionado, além do nível do evento.</span><span class="sxs-lookup"><span data-stu-id="82bdc-106">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="82bdc-107">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="82bdc-107">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="82bdc-108">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="82bdc-108">Keyword for raising the event</span></span>|<span data-ttu-id="82bdc-109">Level</span><span class="sxs-lookup"><span data-stu-id="82bdc-109">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="82bdc-110">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="82bdc-110">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="82bdc-111">Warning (2)</span><span class="sxs-lookup"><span data-stu-id="82bdc-111">Warning (2)</span></span>|  
  
 <span data-ttu-id="82bdc-112">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="82bdc-112">The following table shows event information.</span></span>  
  
|<span data-ttu-id="82bdc-113">Evento</span><span class="sxs-lookup"><span data-stu-id="82bdc-113">Event</span></span>|<span data-ttu-id="82bdc-114">ID do evento</span><span class="sxs-lookup"><span data-stu-id="82bdc-114">Event ID</span></span>|<span data-ttu-id="82bdc-115">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="82bdc-115">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="82bdc-116">80</span><span class="sxs-lookup"><span data-stu-id="82bdc-116">80</span></span>|<span data-ttu-id="82bdc-117">Uma exceção gerenciada é gerada.</span><span class="sxs-lookup"><span data-stu-id="82bdc-117">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="82bdc-118">A tabela a seguir mostra dados do evento.</span><span class="sxs-lookup"><span data-stu-id="82bdc-118">The following table shows event data.</span></span>  
  
|<span data-ttu-id="82bdc-119">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="82bdc-119">Field name</span></span>|<span data-ttu-id="82bdc-120">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="82bdc-120">Data type</span></span>|<span data-ttu-id="82bdc-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="82bdc-121">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="82bdc-122">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="82bdc-122">Exception Type</span></span>|<span data-ttu-id="82bdc-123">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="82bdc-123">win:UnicodeString</span></span>|<span data-ttu-id="82bdc-124">Tipo da exceção; por exemplo, `System.NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="82bdc-124">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="82bdc-125">Mensagem de exceção</span><span class="sxs-lookup"><span data-stu-id="82bdc-125">Exception Message</span></span>|<span data-ttu-id="82bdc-126">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="82bdc-126">win:UnicodeString</span></span>|<span data-ttu-id="82bdc-127">A mensagem de exceção real.</span><span class="sxs-lookup"><span data-stu-id="82bdc-127">Actual exception message.</span></span>|  
|<span data-ttu-id="82bdc-128">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="82bdc-128">EIPCodeThrow</span></span>|<span data-ttu-id="82bdc-129">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="82bdc-129">win:Pointer</span></span>|<span data-ttu-id="82bdc-130">Ponteiro de instrução em que ocorreu a exceção.</span><span class="sxs-lookup"><span data-stu-id="82bdc-130">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="82bdc-131">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="82bdc-131">ExceptionHR</span></span>|<span data-ttu-id="82bdc-132">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="82bdc-132">win:UInt32</span></span>|<span data-ttu-id="82bdc-133">Exceção [HRESULT](https://docs.microsoft.com/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span><span class="sxs-lookup"><span data-stu-id="82bdc-133">Exception [HRESULT](https://docs.microsoft.com/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span></span>|  
|<span data-ttu-id="82bdc-134">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="82bdc-134">ExceptionFlags</span></span>|<span data-ttu-id="82bdc-135">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="82bdc-135">win:UInt16</span></span>|<span data-ttu-id="82bdc-136">0x01: HasInnerException (consulte [Eventos CLR ETW](clr-etw-events.md) na documentação do Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="82bdc-136">0x01: HasInnerException (see [CLR ETW Events](clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="82bdc-137">0x02: IsNestedException.</span><span class="sxs-lookup"><span data-stu-id="82bdc-137">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="82bdc-138">0x04: IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="82bdc-138">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="82bdc-139">0x08: IsCorruptedStateException (indica que o estado do processo está corrompido; consulte [tratamento de exceções de estado corrompido](https://docs.microsoft.com/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span><span class="sxs-lookup"><span data-stu-id="82bdc-139">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](https://docs.microsoft.com/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span></span><br /><br /> <span data-ttu-id="82bdc-140">0x10: IsCLSCompliant (uma exceção que é derivada de <xref:System.Exception> está em conformidade com CLS; caso contrário, ela não está em conformidade com CLS).</span><span class="sxs-lookup"><span data-stu-id="82bdc-140">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="82bdc-141">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="82bdc-141">ClrInstanceID</span></span>|<span data-ttu-id="82bdc-142">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="82bdc-142">win:UInt16</span></span>|<span data-ttu-id="82bdc-143">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="82bdc-143">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="82bdc-144">Confira também</span><span class="sxs-lookup"><span data-stu-id="82bdc-144">See also</span></span>

- [<span data-ttu-id="82bdc-145">Eventos ETW no CLR</span><span class="sxs-lookup"><span data-stu-id="82bdc-145">CLR ETW Events</span></span>](clr-etw-events.md)
