---
title: System.ServiceModel.Channels.FailedAcceptFromPool
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 339ba8df7e782281fcec962ff6c6f01988122b3a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="1bf08-102">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="1bf08-102">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>
<span data-ttu-id="1bf08-103">Falha ao tentar reutilizar uma conexão em pool.</span><span class="sxs-lookup"><span data-stu-id="1bf08-103">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="1bf08-104">Outra tentativa será feita dentro do período de tempo limite especificado.</span><span class="sxs-lookup"><span data-stu-id="1bf08-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1bf08-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="1bf08-105">Description</span></span>  
 <span data-ttu-id="1bf08-106">Este rastreamento informativo indica que ocorreu um erro ao tentar reutilizar uma conexão em pool.</span><span class="sxs-lookup"><span data-stu-id="1bf08-106">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="1bf08-107">Isso pode acontecer porque a conexão em pool não era compatível, pronto ou ainda está ativa.</span><span class="sxs-lookup"><span data-stu-id="1bf08-107">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="1bf08-108">Tentativas adicionais de reutilizar outra conexão em pool são feitas dentro de um determinado tempo de limite e uma conexão nova é criada no caso de nenhuma conexão utilizável é encontrado.</span><span class="sxs-lookup"><span data-stu-id="1bf08-108">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bf08-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1bf08-109">See Also</span></span>  
 [<span data-ttu-id="1bf08-110">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="1bf08-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="1bf08-111">Usando o rastreamento para solucionar problemas de seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="1bf08-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 <span data-ttu-id="1bf08-112">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md) (Administração e diagnósticos)</span><span class="sxs-lookup"><span data-stu-id="1bf08-112">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)</span></span>
