---
title: Interação da política de cache – idade máxima e atualização mínima
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- Revalidate policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- maximum age policy
- minimum freshness policy
- age of cached resources
ms.assetid: 6567d451-ecec-496c-95a3-a415b99ba52a
ms.openlocfilehash: 93136d4c87463db7128a68957b243c1ef13a90eb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59174051"
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a><span data-ttu-id="d9758-102">Interação da política de cache – idade máxima e atualização mínima</span><span class="sxs-lookup"><span data-stu-id="d9758-102">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>
<span data-ttu-id="d9758-103">Para ajudar a garantir que o conteúdo mais atualizado é retornado para o aplicativo cliente, a interação dos requisitos de revalidação do servidor e da política de cache de cliente sempre resulta na política de cache mais conservadora.</span><span class="sxs-lookup"><span data-stu-id="d9758-103">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="d9758-104">Todos os exemplos deste tópico ilustram a política de cache para um recurso que é armazenado em cache em 1º de janeiro e expira em 4 de janeiro.</span><span class="sxs-lookup"><span data-stu-id="d9758-104">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="d9758-105">Os exemplos a seguir ilustram a política de cache que resulta da interação dos valores de idade máxima (`maxAge`) e atualização mínima (`minFresh`).</span><span class="sxs-lookup"><span data-stu-id="d9758-105">The following examples illustrate the cache policy that results from the interaction of the maximum age (`maxAge`) and minimum freshness (`minFresh`) values.</span></span>  
  
-   <span data-ttu-id="d9758-106">Se a política de cache definir `maxAge` = 2 dias e `minFresh` não for especificado, o conteúdo será revalidado em 3 de janeiro.</span><span class="sxs-lookup"><span data-stu-id="d9758-106">If the cache policy sets `maxAge` = 2 days and `minFresh` is not specified, the content is revalidated on January 3.</span></span>  
  
-   <span data-ttu-id="d9758-107">Se a política de cache definir `maxAge` = 2 dias e `minFresh` = 1 dia, de acordo com `maxAge`, o conteúdo ficará atualizado até 3 de janeiro.</span><span class="sxs-lookup"><span data-stu-id="d9758-107">If the cache policy sets `maxAge` = 2 days and `minFresh` = 1 day, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="d9758-108">De acordo com `minFresh`, o conteúdo ficará atualizado até 3 de janeiro.</span><span class="sxs-lookup"><span data-stu-id="d9758-108">According to `minFresh`, the content is fresh until January 3.</span></span> <span data-ttu-id="d9758-109">Portanto, o conteúdo deverá ser revalidado em 3 de janeiro.</span><span class="sxs-lookup"><span data-stu-id="d9758-109">Therefore, the content must be revalidated on January 3.</span></span>  
  
-   <span data-ttu-id="d9758-110">Se a política de cache definir `maxAge` = 2 dias e `minFresh` = 2 dias, de acordo com `maxAge`, o conteúdo ficará atualizado até 3 de janeiro.</span><span class="sxs-lookup"><span data-stu-id="d9758-110">If the cache policy sets `maxAge` = 2 days and `minFresh` = 2 days, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="d9758-111">De acordo com `minFresh`, o conteúdo ficará atualizado até 2 de janeiro.</span><span class="sxs-lookup"><span data-stu-id="d9758-111">According to `minFresh` the content is fresh until January 2.</span></span> <span data-ttu-id="d9758-112">Portanto, o conteúdo deverá ser revalidado em 2 de janeiro.</span><span class="sxs-lookup"><span data-stu-id="d9758-112">Therefore, the content must be revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9758-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9758-113">See also</span></span>

- [<span data-ttu-id="d9758-114">Gerenciamento de cache para aplicativos de rede</span><span class="sxs-lookup"><span data-stu-id="d9758-114">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [<span data-ttu-id="d9758-115">Política de cache</span><span class="sxs-lookup"><span data-stu-id="d9758-115">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)
- [<span data-ttu-id="d9758-116">Políticas de cache baseadas na localização</span><span class="sxs-lookup"><span data-stu-id="d9758-116">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [<span data-ttu-id="d9758-117">Políticas de cache baseadas em tempo</span><span class="sxs-lookup"><span data-stu-id="d9758-117">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [<span data-ttu-id="d9758-118">Configurando o cache em aplicativos de rede</span><span class="sxs-lookup"><span data-stu-id="d9758-118">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)
- [<span data-ttu-id="d9758-119">Interação da política de cache – idade máxima e desatualização máxima</span><span class="sxs-lookup"><span data-stu-id="d9758-119">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)
