---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c7a134a60656c6ee237203b69e1bce40656f13d2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a><span data-ttu-id="c79b6-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span><span class="sxs-lookup"><span data-stu-id="c79b6-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span></span>
<span data-ttu-id="c79b6-103">Ocorreu uma exceção ao fechar as conexões nesse pool de conexão.</span><span class="sxs-lookup"><span data-stu-id="c79b6-103">An exception occurred while closing the connections in this connection pool.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c79b6-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="c79b6-104">Description</span></span>  
 <span data-ttu-id="c79b6-105">Este rastreamento de nível de erro indica que ocorreu um erro ao fechar os pools de conexão usados pelo [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]do recurso do pool de conexão.</span><span class="sxs-lookup"><span data-stu-id="c79b6-105">This error level trace indicates that an error has occurred while closing the connection pools used by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]’s connection pooling feature.</span></span> <span data-ttu-id="c79b6-106">Um motivo possível para isso é um feriado bem-sucedida de uma conexão em pool ou um conjunto de conexões em pool dentro de CloseTimeout.</span><span class="sxs-lookup"><span data-stu-id="c79b6-106">One possible reason for this is an unsuccessful closure of a pooled connection, or a set of pooled connections within the CloseTimeout.</span></span> <span data-ttu-id="c79b6-107">Quando essa exceção é gerada, quaisquer conexões restantes não fechadas dentro desse pool foram anuladas; conexões não fechadas dentro de outros pools são abandonadas.</span><span class="sxs-lookup"><span data-stu-id="c79b6-107">When this exception is thrown, any remaining unclosed connections within that pool are aborted; unclosed connections within other pools are abandoned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c79b6-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c79b6-108">See Also</span></span>  
 [<span data-ttu-id="c79b6-109">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="c79b6-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="c79b6-110">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="c79b6-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="c79b6-111">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="c79b6-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
