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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0ea98388efe14ac0d18a94ec056a441096a4d7c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a><span data-ttu-id="19ff1-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span><span class="sxs-lookup"><span data-stu-id="19ff1-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span></span>
<span data-ttu-id="19ff1-103">Ocorreu uma exceção ao fechar as conexões nesse pool de conexão.</span><span class="sxs-lookup"><span data-stu-id="19ff1-103">An exception occurred while closing the connections in this connection pool.</span></span>  
  
## <a name="description"></a><span data-ttu-id="19ff1-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="19ff1-104">Description</span></span>  
 <span data-ttu-id="19ff1-105">Este rastreamento de nível de erro indica que ocorreu um erro ao fechar os pools de conexão usados pelo [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]do recurso do pool de conexão.</span><span class="sxs-lookup"><span data-stu-id="19ff1-105">This error level trace indicates that an error has occurred while closing the connection pools used by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]’s connection pooling feature.</span></span> <span data-ttu-id="19ff1-106">Um motivo possível para isso é um feriado bem-sucedida de uma conexão em pool ou um conjunto de conexões em pool dentro de CloseTimeout.</span><span class="sxs-lookup"><span data-stu-id="19ff1-106">One possible reason for this is an unsuccessful closure of a pooled connection, or a set of pooled connections within the CloseTimeout.</span></span> <span data-ttu-id="19ff1-107">Quando essa exceção é gerada, quaisquer conexões restantes não fechadas dentro desse pool foram anuladas; conexões não fechadas dentro de outros pools são abandonadas.</span><span class="sxs-lookup"><span data-stu-id="19ff1-107">When this exception is thrown, any remaining unclosed connections within that pool are aborted; unclosed connections within other pools are abandoned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19ff1-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="19ff1-108">See Also</span></span>  
 [<span data-ttu-id="19ff1-109">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="19ff1-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="19ff1-110">Usando o rastreamento para solucionar problemas de seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="19ff1-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 <span data-ttu-id="19ff1-111">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md) (Administração e diagnósticos)</span><span class="sxs-lookup"><span data-stu-id="19ff1-111">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)</span></span>
