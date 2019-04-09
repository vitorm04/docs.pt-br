---
title: System.ServiceModel.Channels.FailedAcceptFromPool
ms.date: 03/30/2017
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
ms.openlocfilehash: de0bdd9e5ab922b09249bf550fde745042be8e58
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156475"
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="88c96-102">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="88c96-102">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>
<span data-ttu-id="88c96-103">Falha ao tentar reutilizar uma conexão em pool.</span><span class="sxs-lookup"><span data-stu-id="88c96-103">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="88c96-104">Outra tentativa é feita dentro do período de tempo limite especificado.</span><span class="sxs-lookup"><span data-stu-id="88c96-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="88c96-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="88c96-105">Description</span></span>  
 <span data-ttu-id="88c96-106">Este rastreamento informativo indica que ocorreu um erro durante a tentativa de reutilizar uma conexão em pool.</span><span class="sxs-lookup"><span data-stu-id="88c96-106">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="88c96-107">Isso pode acontecer porque a conexão em pool não era compatível, pronto ou ainda está ativa.</span><span class="sxs-lookup"><span data-stu-id="88c96-107">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="88c96-108">Tentativas adicionais de reutilizar outra conexão em pool são feitas dentro do tempo limite determinado e uma conexão nova é criada, caso nenhuma conexão utilizável é encontrado.</span><span class="sxs-lookup"><span data-stu-id="88c96-108">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88c96-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88c96-109">See also</span></span>

- [<span data-ttu-id="88c96-110">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="88c96-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="88c96-111">Utilizando o rastreamento para solucionar problemas em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="88c96-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="88c96-112">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="88c96-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
