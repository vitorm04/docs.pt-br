---
title: System.ServiceModel.Channels.FailedAcceptFromPool
ms.date: 03/30/2017
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
ms.openlocfilehash: 5bfa31d0eaf3b00017512eddc60bfa99eda619e3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84582576"
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="8c1ab-102">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="8c1ab-102">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>
<span data-ttu-id="8c1ab-103">Falha ao tentar reutilizar uma conexão em pool.</span><span class="sxs-lookup"><span data-stu-id="8c1ab-103">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="8c1ab-104">Outra tentativa é feita dentro do período de tempo limite especificado.</span><span class="sxs-lookup"><span data-stu-id="8c1ab-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8c1ab-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="8c1ab-105">Description</span></span>  
 <span data-ttu-id="8c1ab-106">Esse rastreamento informativo indica que ocorreu um erro ao tentar reutilizar uma conexão em pool.</span><span class="sxs-lookup"><span data-stu-id="8c1ab-106">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="8c1ab-107">Isso pode acontecer porque a conexão em pool não era compatível, pronta ou ainda está ativa.</span><span class="sxs-lookup"><span data-stu-id="8c1ab-107">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="8c1ab-108">As tentativas adicionais de reutilização de outra conexão em pool são feitas dentro de um determinado tempo limite e uma nova conexão é criada caso não sejam encontradas conexões utilizáveis.</span><span class="sxs-lookup"><span data-stu-id="8c1ab-108">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c1ab-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8c1ab-109">See also</span></span>

- [<span data-ttu-id="8c1ab-110">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="8c1ab-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="8c1ab-111">Utilizando o rastreamento para solucionar problemas em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="8c1ab-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="8c1ab-112">Administração e diagnóstico</span><span class="sxs-lookup"><span data-stu-id="8c1ab-112">Administration and Diagnostics</span></span>](../index.md)
