---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: 3dd28276cd3a39497c0387f5b9d0adec23d07c37
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666827"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a><span data-ttu-id="a4ccc-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span><span class="sxs-lookup"><span data-stu-id="a4ccc-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span></span>
<span data-ttu-id="a4ccc-103">Ocorreu uma exceção ao fechar as conexões nesse pool de conexão.</span><span class="sxs-lookup"><span data-stu-id="a4ccc-103">An exception occurred while closing the connections in this connection pool.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a4ccc-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="a4ccc-104">Description</span></span>  
 <span data-ttu-id="a4ccc-105">Rastreamento de nível de erro indica que ocorreu um erro ao fechar os pools de conexão usados pela conexão Windows Communication Foundation (WCF) do pool de recursos.</span><span class="sxs-lookup"><span data-stu-id="a4ccc-105">This error level trace indicates that an error has occurred while closing the connection pools used by Windows Communication Foundation (WCF)’s connection pooling feature.</span></span> <span data-ttu-id="a4ccc-106">Um motivo possível para isso é um fechamento malsucedido de uma conexão em pool ou um conjunto de conexões em pool dentro de CloseTimeout.</span><span class="sxs-lookup"><span data-stu-id="a4ccc-106">One possible reason for this is an unsuccessful closure of a pooled connection, or a set of pooled connections within the CloseTimeout.</span></span> <span data-ttu-id="a4ccc-107">Quando essa exceção é lançada, quaisquer conexões não fechadas restantes no pool são anuladas; conexões não fechadas dentro de outros pools são abandonadas.</span><span class="sxs-lookup"><span data-stu-id="a4ccc-107">When this exception is thrown, any remaining unclosed connections within that pool are aborted; unclosed connections within other pools are abandoned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4ccc-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a4ccc-108">See also</span></span>

- [<span data-ttu-id="a4ccc-109">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="a4ccc-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="a4ccc-110">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="a4ccc-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="a4ccc-111">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="a4ccc-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
