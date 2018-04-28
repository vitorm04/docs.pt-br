---
title: Atividades de manipulação de erro de WF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 24b68bd3-cef5-4413-ab82-2e2625f209aa
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1c0459dd562f6292a8fe9a42f8b1b48cd175516a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="error-handling-activities-in-wf"></a><span data-ttu-id="88fb6-102">Atividades de manipulação de erro de WF</span><span class="sxs-lookup"><span data-stu-id="88fb6-102">Error Handling Activities in WF</span></span>
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<span data-ttu-id="88fb6-103"> fornece vários sistema forneceu atividades implementando o tratamento de erro e recuperação.</span><span class="sxs-lookup"><span data-stu-id="88fb6-103"> provides several system-provided activities for implementing error handling and recovery.</span></span> <span data-ttu-id="88fb6-104">Para obter mais informações, consulte [exceções](../../../docs/framework/windows-workflow-foundation/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="88fb6-104">For more information, see [Exceptions](../../../docs/framework/windows-workflow-foundation/exceptions.md).</span></span>  
  
## <a name="error-handling-activities"></a><span data-ttu-id="88fb6-105">Atividades de tratamento de erro</span><span class="sxs-lookup"><span data-stu-id="88fb6-105">Error handling activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|<span data-ttu-id="88fb6-106">Qual a exceção a última lançada de uma atividade de `TryCatch` .</span><span class="sxs-lookup"><span data-stu-id="88fb6-106">Rethrows the last exception thrown from within a `TryCatch` activity.</span></span>|  
|<xref:System.Activities.Statements.Throw>|<span data-ttu-id="88fb6-107">Gerencie uma exceção.</span><span class="sxs-lookup"><span data-stu-id="88fb6-107">Throws an exception.</span></span>|  
|<xref:System.Activities.Statements.TryCatch>|<span data-ttu-id="88fb6-108">Implementa manipulação de exceção.</span><span class="sxs-lookup"><span data-stu-id="88fb6-108">Implements exception handling.</span></span>|
