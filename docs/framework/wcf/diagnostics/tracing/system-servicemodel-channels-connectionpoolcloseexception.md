---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: f3474fc1bb0ed0d11df6289ed6470447d815f5ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33475745"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a><span data-ttu-id="faf7a-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span><span class="sxs-lookup"><span data-stu-id="faf7a-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span></span>
<span data-ttu-id="faf7a-103">Ocorreu uma exceção ao fechar as conexões nesse pool de conexão.</span><span class="sxs-lookup"><span data-stu-id="faf7a-103">An exception occurred while closing the connections in this connection pool.</span></span>  
  
## <a name="description"></a><span data-ttu-id="faf7a-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="faf7a-104">Description</span></span>  
 <span data-ttu-id="faf7a-105">Este rastreamento de nível de erro indica que ocorreu um erro ao fechar os pools de conexão usados pela conexão do Windows Communication Foundation (WCF) do pool de recursos.</span><span class="sxs-lookup"><span data-stu-id="faf7a-105">This error level trace indicates that an error has occurred while closing the connection pools used by Windows Communication Foundation (WCF)’s connection pooling feature.</span></span> <span data-ttu-id="faf7a-106">Um motivo possível para isso é um feriado bem-sucedida de uma conexão em pool ou um conjunto de conexões em pool dentro de CloseTimeout.</span><span class="sxs-lookup"><span data-stu-id="faf7a-106">One possible reason for this is an unsuccessful closure of a pooled connection, or a set of pooled connections within the CloseTimeout.</span></span> <span data-ttu-id="faf7a-107">Quando essa exceção é gerada, quaisquer conexões restantes não fechadas dentro desse pool foram anuladas; conexões não fechadas dentro de outros pools são abandonadas.</span><span class="sxs-lookup"><span data-stu-id="faf7a-107">When this exception is thrown, any remaining unclosed connections within that pool are aborted; unclosed connections within other pools are abandoned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faf7a-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="faf7a-108">See Also</span></span>  
 [<span data-ttu-id="faf7a-109">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="faf7a-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="faf7a-110">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="faf7a-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="faf7a-111">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="faf7a-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
