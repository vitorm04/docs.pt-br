---
title: System.ServiceModel.Channels.FailedAcceptFromPool
ms.date: 03/30/2017
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
ms.openlocfilehash: 59bba87095931c80a7ce347def2656a7a1f6f949
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="cf6a0-102">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="cf6a0-102">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>
<span data-ttu-id="cf6a0-103">Falha ao tentar reutilizar uma conexão em pool.</span><span class="sxs-lookup"><span data-stu-id="cf6a0-103">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="cf6a0-104">Outra tentativa será feita dentro do período de tempo limite especificado.</span><span class="sxs-lookup"><span data-stu-id="cf6a0-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="cf6a0-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="cf6a0-105">Description</span></span>  
 <span data-ttu-id="cf6a0-106">Este rastreamento informativo indica que ocorreu um erro ao tentar reutilizar uma conexão em pool.</span><span class="sxs-lookup"><span data-stu-id="cf6a0-106">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="cf6a0-107">Isso pode acontecer porque a conexão em pool não era compatível, pronto ou ainda está ativa.</span><span class="sxs-lookup"><span data-stu-id="cf6a0-107">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="cf6a0-108">Tentativas adicionais de reutilizar outra conexão em pool são feitas dentro de um determinado tempo de limite e uma conexão nova é criada no caso de nenhuma conexão utilizável é encontrado.</span><span class="sxs-lookup"><span data-stu-id="cf6a0-108">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf6a0-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf6a0-109">See Also</span></span>  
 [<span data-ttu-id="cf6a0-110">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="cf6a0-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="cf6a0-111">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="cf6a0-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="cf6a0-112">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="cf6a0-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
