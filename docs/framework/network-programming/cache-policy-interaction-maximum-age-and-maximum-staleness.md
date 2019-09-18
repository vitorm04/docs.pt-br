---
title: Interação da política de cache – idade máxima e desatualização máxima
ms.date: 03/30/2017
helpviewer_keywords:
- maximum staleness
- freshness of cached resources
- time, cached resources
- maximum age policy
- staleness of cached resources
- age of cached resources
ms.assetid: 7f775925-89a1-4956-ba90-c869c1749a94
ms.openlocfilehash: e21cfc28407ba67afdce8d72e5e52c12ab359059
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048836"
---
# <a name="cache-policy-interactionmaximum-age-and-maximum-staleness"></a><span data-ttu-id="0618f-102">Interação da política de cache – idade máxima e desatualização máxima</span><span class="sxs-lookup"><span data-stu-id="0618f-102">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>
<span data-ttu-id="0618f-103">Para ajudar a garantir que o conteúdo mais atualizado é retornado para o aplicativo cliente, a interação dos requisitos de revalidação do servidor e da política de cache de cliente sempre resulta na política de cache mais conservadora.</span><span class="sxs-lookup"><span data-stu-id="0618f-103">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="0618f-104">Todos os exemplos deste tópico ilustram a política de cache para um recurso que é armazenado em cache em 1º de janeiro e expira em 4 de janeiro.</span><span class="sxs-lookup"><span data-stu-id="0618f-104">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="0618f-105">Nos seguintes exemplos, o valor máximo de desatualização (`maxStale`) é usado em conjunto com uma idade máxima (`maxAge`):</span><span class="sxs-lookup"><span data-stu-id="0618f-105">In the following examples, the maximum staleness value (`maxStale`) is used in conjunction with a maximum age (`maxAge`):</span></span>  
  
- <span data-ttu-id="0618f-106">Se a política de cache definir `maxAge` = 5 dias e não especificar um valor `maxStale`, de acordo com o valor `maxAge`, o conteúdo será utilizável até 6 de janeiro.</span><span class="sxs-lookup"><span data-stu-id="0618f-106">If the cache policy sets `maxAge` = 5 days and does not specify a `maxStale` value, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="0618f-107">No entanto, de acordo com os requisitos de revalidação do servidor, o conteúdo expirará em 4 de janeiro.</span><span class="sxs-lookup"><span data-stu-id="0618f-107">However, according to the server's revalidation requirements, the content expires on January 4.</span></span> <span data-ttu-id="0618f-108">Como a data de expiração do conteúdo é mais conservadora (anterior), ela terá precedência sobre a política `maxAge`.</span><span class="sxs-lookup"><span data-stu-id="0618f-108">Because the content expiration date is more conservative (sooner), it takes precedence over the `maxAge` policy.</span></span> <span data-ttu-id="0618f-109">Portanto, o conteúdo expirará em 4 de janeiro e deverá ser revalidado, embora sua idade máxima não tenha sido atingida.</span><span class="sxs-lookup"><span data-stu-id="0618f-109">Therefore, the content expires on January 4 and must be revalidated even though its maximum age has not been reached.</span></span>  
  
- <span data-ttu-id="0618f-110">Se a política de cache definir `maxAge` = 5 dias e `maxStale` = 3 dias, de acordo com o valor `maxAge`, o conteúdo será utilizável até 6 de janeiro.</span><span class="sxs-lookup"><span data-stu-id="0618f-110">If the cache policy sets `maxAge` = 5 days and `maxStale` = 3 days, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="0618f-111">De acordo com o valor `maxStale`, o conteúdo será utilizável até 7 de janeiro.</span><span class="sxs-lookup"><span data-stu-id="0618f-111">According to the `maxStale` value, the content is usable until January 7.</span></span> <span data-ttu-id="0618f-112">Portanto, o conteúdo será revalidado em 6 de janeiro.</span><span class="sxs-lookup"><span data-stu-id="0618f-112">Therefore, the content gets revalidated on January 6.</span></span>  
  
- <span data-ttu-id="0618f-113">Se a política de cache definir `maxAge` = 5 dias e `maxStale` = 1 dia, de acordo com o valor `maxAge`, o conteúdo será utilizável até 6 de janeiro.</span><span class="sxs-lookup"><span data-stu-id="0618f-113">If the cache policy sets `maxAge` = 5 days and `maxStale` = 1 day, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="0618f-114">De acordo com o valor `maxStale`, o conteúdo será utilizável até 5 de janeiro.</span><span class="sxs-lookup"><span data-stu-id="0618f-114">According to the `maxStale` value, the content is usable until January 5.</span></span> <span data-ttu-id="0618f-115">Portanto, o conteúdo será revalidado em 5 de janeiro.</span><span class="sxs-lookup"><span data-stu-id="0618f-115">Therefore, the content gets revalidated on January 5.</span></span>  
  
 <span data-ttu-id="0618f-116">Quando a idade máxima for menor que a data de expiração do conteúdo, o comportamento de cache mais conservador sempre prevalecerá e o valor máximo de desatualização não terá nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="0618f-116">When the maximum age is less than the content expiration date, the more conservative caching behavior always prevails and the maximum staleness value has no effect.</span></span> <span data-ttu-id="0618f-117">Os seguintes exemplos ilustram o efeito de definir um valor máximo de desatualização (`maxStale`) quando a idade máxima (`maxAge`) for atingida antes da expiração do conteúdo:</span><span class="sxs-lookup"><span data-stu-id="0618f-117">The following examples illustrate the effect of setting a maximum staleness (`maxStale`) value when the maximum age (`maxAge`) is reached before the content expires:</span></span>  
  
- <span data-ttu-id="0618f-118">Se a política de cache definir `maxAge` = 1 dia e não especificar um valor para o valor `maxStale`, o conteúdo será revalidado em 2 de janeiro, mesmo que não tenha expirado.</span><span class="sxs-lookup"><span data-stu-id="0618f-118">If the cache policy sets `maxAge` = 1 day and does not specify a value for `maxStale` value, the content is revalidated on January 2 even though it has not expired.</span></span>  
  
- <span data-ttu-id="0618f-119">Se a política de cache definir `maxAge` = 1 dia e `maxStale` = 3 dias, o conteúdo será revalidado em 2 de janeiro para impor a configuração de política mais conservadora.</span><span class="sxs-lookup"><span data-stu-id="0618f-119">If the cache policy sets `maxAge` = 1 day and `maxStale` = 3 days, the content is revalidated on January 2 to enforce the more conservative policy setting.</span></span>  
  
- <span data-ttu-id="0618f-120">Se a política de cache definir `maxAge` = 1 dia e `maxStale` = 1 dia, o conteúdo será revalidado em 2 de janeiro.</span><span class="sxs-lookup"><span data-stu-id="0618f-120">If the cache policy sets `maxAge` = 1 day and `maxStale` = 1 day, the content is revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0618f-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0618f-121">See also</span></span>

- [<span data-ttu-id="0618f-122">Gerenciamento de cache para aplicativos de rede</span><span class="sxs-lookup"><span data-stu-id="0618f-122">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="0618f-123">Política de cache</span><span class="sxs-lookup"><span data-stu-id="0618f-123">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="0618f-124">Políticas de cache baseadas na localização</span><span class="sxs-lookup"><span data-stu-id="0618f-124">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="0618f-125">Políticas de cache baseadas em tempo</span><span class="sxs-lookup"><span data-stu-id="0618f-125">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="0618f-126">Configurando o cache em aplicativos de rede</span><span class="sxs-lookup"><span data-stu-id="0618f-126">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)
- [<span data-ttu-id="0618f-127">Interação da política de cache – idade máxima e atualização mínima</span><span class="sxs-lookup"><span data-stu-id="0618f-127">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>](cache-policy-interaction-maximum-age-and-minimum-freshness.md)
