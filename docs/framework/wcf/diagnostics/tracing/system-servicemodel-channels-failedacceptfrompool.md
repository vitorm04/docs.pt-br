---
title: System.ServiceModel.Channels.FailedAcceptFromPool
ms.date: 03/30/2017
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
ms.openlocfilehash: 093a76a0157948520c2f0d8bf6145b6f78966906
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54695459"
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="84bcc-102">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="84bcc-102">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>
<span data-ttu-id="84bcc-103">Falha ao tentar reutilizar uma conexão em pool.</span><span class="sxs-lookup"><span data-stu-id="84bcc-103">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="84bcc-104">Outra tentativa é feita dentro do período de tempo limite especificado.</span><span class="sxs-lookup"><span data-stu-id="84bcc-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="84bcc-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="84bcc-105">Description</span></span>  
 <span data-ttu-id="84bcc-106">Este rastreamento informativo indica que ocorreu um erro durante a tentativa de reutilizar uma conexão em pool.</span><span class="sxs-lookup"><span data-stu-id="84bcc-106">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="84bcc-107">Isso pode acontecer porque a conexão em pool não era compatível, pronto ou ainda está ativa.</span><span class="sxs-lookup"><span data-stu-id="84bcc-107">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="84bcc-108">Tentativas adicionais de reutilizar outra conexão em pool são feitas dentro do tempo limite determinado e uma conexão nova é criada, caso nenhuma conexão utilizável é encontrado.</span><span class="sxs-lookup"><span data-stu-id="84bcc-108">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84bcc-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84bcc-109">See also</span></span>
- [<span data-ttu-id="84bcc-110">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="84bcc-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="84bcc-111">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="84bcc-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="84bcc-112">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="84bcc-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
