---
title: CoordinatorRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
ms.openlocfilehash: de9d27e74088b1bac9c8a401c5af2b119fc8e90e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797977"
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="1d792-102">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="1d792-102">CoordinatorRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="1d792-103">Sessão 139</span><span class="sxs-lookup"><span data-stu-id="1d792-103">Id: 139</span></span>  
  
 <span data-ttu-id="1d792-104">Severity Erro</span><span class="sxs-lookup"><span data-stu-id="1d792-104">Severity: Error</span></span>  
  
 <span data-ttu-id="1d792-105">Categorias TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="1d792-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="1d792-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="1d792-106">Description</span></span>  
 <span data-ttu-id="1d792-107">Esse evento indica que uma entrada de log de recuperação do coordenador foi corrompida e não pôde ser desserializada.</span><span class="sxs-lookup"><span data-stu-id="1d792-107">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="1d792-108">A perda de dados pode resultar desse erro.</span><span class="sxs-lookup"><span data-stu-id="1d792-108">Data loss may result from this error.</span></span> <span data-ttu-id="1d792-109">O evento lista a ID da transação, os dados de recuperação (codificado na Base64), a exceção, o nome do processo e a ID do processo.</span><span class="sxs-lookup"><span data-stu-id="1d792-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d792-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d792-110">See also</span></span>

- [<span data-ttu-id="1d792-111">Registro de eventos em log</span><span class="sxs-lookup"><span data-stu-id="1d792-111">Event Logging</span></span>](index.md)
- [<span data-ttu-id="1d792-112">Referência geral de eventos</span><span class="sxs-lookup"><span data-stu-id="1d792-112">Events General Reference</span></span>](events-general-reference.md)
