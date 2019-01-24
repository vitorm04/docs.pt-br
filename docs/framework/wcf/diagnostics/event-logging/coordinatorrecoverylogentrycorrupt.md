---
title: CoordinatorRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
ms.openlocfilehash: 0dc74b784d8a9ed3ab27bb4b8d3de34143f6ce07
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54639478"
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="b9d12-102">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="b9d12-102">CoordinatorRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="b9d12-103">Id: 139</span><span class="sxs-lookup"><span data-stu-id="b9d12-103">Id: 139</span></span>  
  
 <span data-ttu-id="b9d12-104">Gravidade: Erro</span><span class="sxs-lookup"><span data-stu-id="b9d12-104">Severity: Error</span></span>  
  
 <span data-ttu-id="b9d12-105">Categoria: TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="b9d12-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="b9d12-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="b9d12-106">Description</span></span>  
 <span data-ttu-id="b9d12-107">Esse evento indica que uma entrada de log de recuperação do coordenador foi corrompida e não pôde ser desserializada.</span><span class="sxs-lookup"><span data-stu-id="b9d12-107">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="b9d12-108">Esse erro, pode causar perda de dados.</span><span class="sxs-lookup"><span data-stu-id="b9d12-108">Data loss may result from this error.</span></span> <span data-ttu-id="b9d12-109">A ID da transação de listas de eventos, dados de recuperação (codificado em Base64), exceção, nome do processo e processo de identificação.</span><span class="sxs-lookup"><span data-stu-id="b9d12-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9d12-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b9d12-110">See also</span></span>
- [<span data-ttu-id="b9d12-111">Registro de eventos em log</span><span class="sxs-lookup"><span data-stu-id="b9d12-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)
- [<span data-ttu-id="b9d12-112">Referência geral de eventos</span><span class="sxs-lookup"><span data-stu-id="b9d12-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
