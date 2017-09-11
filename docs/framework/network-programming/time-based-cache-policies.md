---
title: "Políticas de cache baseadas em tempo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- time-based cache policies
- cache synchronization date policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- time, cached resources
- maximum age policy
- synchronization, cache
- staleness of cached resources
- default time-based cache policy
- maximum staleness policy
- content cache policies
- expired content
- minimum freshness policy
- age of cached resources
ms.assetid: 74f0bcaf-5c95-40c1-9967-f3bbf1d2360a
caps.latest.revision: 11
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2915139d6a3c46de06bd2bdb0cb12f95f611af3b
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="time-based-cache-policies"></a><span data-ttu-id="65c9d-102">Políticas de cache baseadas em tempo</span><span class="sxs-lookup"><span data-stu-id="65c9d-102">Time-Based Cache Policies</span></span>
<span data-ttu-id="65c9d-103">Uma política de cache baseada em tempo define a atualização das entradas armazenadas em cache usando a hora em que o recurso foi recuperado, os cabeçalhos retornados com o recurso e a hora atual.</span><span class="sxs-lookup"><span data-stu-id="65c9d-103">A time-based cache policy defines the freshness of cached entries using the time the resource was retrieved, the headers returned with the resource, and the current time.</span></span> <span data-ttu-id="65c9d-104">Ao definir uma política de cache baseada em tempo, é possível usar a política baseada em tempo de <xref:System.Net.Cache.HttpRequestCacheLevel.Default> ou criar uma política baseada em tempo personalizada.</span><span class="sxs-lookup"><span data-stu-id="65c9d-104">When setting a time-based cache policy, you can either use the <xref:System.Net.Cache.HttpRequestCacheLevel.Default> time-based policy or create a customized time-based policy.</span></span> <span data-ttu-id="65c9d-105">Ao usar a política baseada em tempo padrão para os recursos obtidos com o uso do protocolo HTTP, o comportamento de cache exato é determinado pelos cabeçalhos incluídos na resposta armazenada em cache e pelos comportamentos especificados nas seções 13 e 14 do RFC 2616, disponível em [http://www.ietf.org](http://www.ietf.org/). Para obter um exemplo de código que demonstra a configuração da política baseada em tempo padrão para recursos HTTP, consulte [Como definir a política de cache baseada em tempo padrão de um aplicativo](../../../docs/framework/network-programming/how-to-set-the-default-time-based-cache-policy-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="65c9d-105">When using the default time-based policy for resources obtained using Hypertext Transfer Protocol (HTTP), the exact cache behavior is determined by the headers included in the cached response and by the behaviors specified in sections 13 and 14 of RFC 2616, available at [http://www.ietf.org](http://www.ietf.org/). For a code example that demonstrates setting the default time-based policy for HTTP resources, see [How to: Set the Default Time-Based Cache Policy for an Application](../../../docs/framework/network-programming/how-to-set-the-default-time-based-cache-policy-for-an-application.md).</span></span> <span data-ttu-id="65c9d-106">Para obter exemplos de código que demonstram como criar e usar políticas de cache, consulte [Configurando o cache em aplicativos de rede](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md).</span><span class="sxs-lookup"><span data-stu-id="65c9d-106">For code examples that demonstrate creating and using cache policies, see [Configuring Caching in Network Applications](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md).</span></span>  
  
## <a name="criteria-to-determine-freshness-of-cached-entries"></a><span data-ttu-id="65c9d-107">Critérios para determinar a atualização das entradas armazenadas em cache</span><span class="sxs-lookup"><span data-stu-id="65c9d-107">Criteria to Determine Freshness of Cached Entries</span></span>  
 <span data-ttu-id="65c9d-108">Para personalizar uma política de cache baseada em tempo, especifique o uso de um ou mais dos seguintes critérios para determinar a atualização das entradas armazenadas em cache:</span><span class="sxs-lookup"><span data-stu-id="65c9d-108">To customize a time-based cache policy, you can specify that one or more of the following criteria be used to determine the freshness of cached entries:</span></span>  
  
-   <span data-ttu-id="65c9d-109">Idade máxima</span><span class="sxs-lookup"><span data-stu-id="65c9d-109">Maximum age</span></span>  
  
-   <span data-ttu-id="65c9d-110">Desatualização máxima</span><span class="sxs-lookup"><span data-stu-id="65c9d-110">Maximum staleness</span></span>  
  
-   <span data-ttu-id="65c9d-111">Atualização mínima</span><span class="sxs-lookup"><span data-stu-id="65c9d-111">Minimum freshness</span></span>  
  
-   <span data-ttu-id="65c9d-112">Data de sincronização do cache</span><span class="sxs-lookup"><span data-stu-id="65c9d-112">Cache synchronization date</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="65c9d-113">O uso da política de cache baseada em tempo padrão não deve ser confundido com a configuração de uma política de cache padrão para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="65c9d-113">Using the default time-based cache policy should not be confused with setting a default cache policy for your application.</span></span> <span data-ttu-id="65c9d-114">A política baseada em tempo padrão é uma política específica que pode ser usada no nível da solicitação ou do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="65c9d-114">The default time-based policy is a specific policy that can be used at the request or application level.</span></span> <span data-ttu-id="65c9d-115">A política de cache padrão do aplicativo é uma política (baseada na localização ou em tempo) que entra em vigor quando nenhuma política é definida em uma solicitação.</span><span class="sxs-lookup"><span data-stu-id="65c9d-115">The default cache policy for your application is a policy (location-based or time-based) that takes effect when no policy is set on a request.</span></span> <span data-ttu-id="65c9d-116">Para obter detalhes sobre como definir uma política de cache padrão para o aplicativo, consulte <xref:System.Net.WebRequest.DefaultCachePolicy%2A>.</span><span class="sxs-lookup"><span data-stu-id="65c9d-116">For details on setting a default cache policy for your application, see <xref:System.Net.WebRequest.DefaultCachePolicy%2A>.</span></span>  
  
### <a name="maximum-age"></a><span data-ttu-id="65c9d-117">Idade Máxima</span><span class="sxs-lookup"><span data-stu-id="65c9d-117">Maximum Age</span></span>  
 <span data-ttu-id="65c9d-118">O critério de política de idade máxima especifica o tempo durante o qual uma cópia armazenada em cache de um recurso pode ser usada.</span><span class="sxs-lookup"><span data-stu-id="65c9d-118">The maximum age policy criterion specifies the amount of time a cached copy of a resource can be used.</span></span> <span data-ttu-id="65c9d-119">Se a cópia armazenada em cache do recurso for mais antiga que o tempo especificado, o recurso deverá ser revalidado com sua verificação em relação ao conteúdo no servidor.</span><span class="sxs-lookup"><span data-stu-id="65c9d-119">If the cached copy of the resource is older than the amount of time specified, the resource must be revalidated by checking it against the content on the server.</span></span> <span data-ttu-id="65c9d-120">Se a idade máxima permitir que o recurso seja usado depois que ele expirar, esse critério não será respeitado, a menos que um valor de desatualização máxima também seja especificado.</span><span class="sxs-lookup"><span data-stu-id="65c9d-120">If the maximum age would allow the resource to be used after it expires, this criteria is not honored unless a maximum staleness value is also specified.</span></span>  
  
### <a name="maximum-staleness"></a><span data-ttu-id="65c9d-121">Desatualização Máxima</span><span class="sxs-lookup"><span data-stu-id="65c9d-121">Maximum Staleness</span></span>  
 <span data-ttu-id="65c9d-122">O critério de política de desatualização máxima especifica o tempo durante o qual a cópia armazenada em cache do recurso pode ser usada após a expiração do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="65c9d-122">The maximum staleness policy criterion specifies the length of time after content expiration that the cached copy of the resource can be used.</span></span> <span data-ttu-id="65c9d-123">Esse é o único critério de política de cache que permite que os recursos sejam usados depois de terem expirado.</span><span class="sxs-lookup"><span data-stu-id="65c9d-123">This is the only cache policy criterion that permits resources to be used after they have expired.</span></span>  
  
### <a name="minimum-freshness"></a><span data-ttu-id="65c9d-124">Atualização Mínima</span><span class="sxs-lookup"><span data-stu-id="65c9d-124">Minimum Freshness</span></span>  
 <span data-ttu-id="65c9d-125">O critério de política de atualização mínima especifica o tempo durante o qual a cópia armazenada em cache do recurso pode ser usada antes da expiração do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="65c9d-125">The minimum freshness policy criterion specifies the length of time before content expiration that the cached copy of the resource can be used.</span></span> <span data-ttu-id="65c9d-126">Essa política tem o efeito de fazer com que uma entrada de cache expire antes da data de expiração; portanto, as configurações de atualização mínima e desatualização máxima são mutuamente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="65c9d-126">This policy has the effect of causing a cache entry to expire before its expiration date; therefore, the minimum freshness and maximum staleness settings are mutually exclusive.</span></span>  
  
## <a name="cache-synchronization-date"></a><span data-ttu-id="65c9d-127">Data de Sincronização do Cache</span><span class="sxs-lookup"><span data-stu-id="65c9d-127">Cache Synchronization Date</span></span>  
 <span data-ttu-id="65c9d-128">O critério de política de data de sincronização do cache determina quando uma cópia armazenada em cache de um recurso deve ser revalidada com sua verificação em relação ao conteúdo no servidor.</span><span class="sxs-lookup"><span data-stu-id="65c9d-128">The cache synchronization date policy criterion determines when a cached copy of a resource must be revalidated by checking it against the content on the server.</span></span> <span data-ttu-id="65c9d-129">Se o conteúdo foi alterado desde que o item foi armazenado em cache, ele é recuperado do servidor, armazenado no cache e retornado ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="65c9d-129">If the content has changed since the item was cached, it is retrieved from the server, stored in the cache, and returned to the application.</span></span> <span data-ttu-id="65c9d-130">Se o conteúdo não foi alterado, seu carimbo de data/hora é atualizado e o aplicativo obtém o conteúdo armazenado em cache.</span><span class="sxs-lookup"><span data-stu-id="65c9d-130">If the content has not changed, its timestamp is updated and the application gets the cached content.</span></span>  
  
 <span data-ttu-id="65c9d-131">A data de sincronização do cache permite especificar uma data absoluta quando o conteúdo armazenado em cache deve ser revalidado.</span><span class="sxs-lookup"><span data-stu-id="65c9d-131">The cache synchronization date allows you to specify an absolute date when cached contents must be revalidated.</span></span> <span data-ttu-id="65c9d-132">Se uma entrada de cache atualizada foi revalidada pela última vez antes da data de sincronização do cache, a revalidação com o servidor ainda ocorrerá.</span><span class="sxs-lookup"><span data-stu-id="65c9d-132">If a fresh cache entry was last revalidated prior to the cache synchronization date, revalidation with the server still occurs.</span></span> <span data-ttu-id="65c9d-133">Se a entrada de cache foi revalidada após a data de sincronização do cache e não houver nenhuma atualização adicional nem requisitos de revalidação do servidor que invalidam a entrada armazenada em cache, a entrada do cache será usada.</span><span class="sxs-lookup"><span data-stu-id="65c9d-133">If the cache entry was revalidated after the cache synchronization date and there are no additional freshness or server revalidation requirements that invalidate the cached entry, the entry from the cache is used.</span></span> <span data-ttu-id="65c9d-134">Se a data de sincronização do cache for definida como uma data futura, a entrada será revalidada sempre que solicitado, até que a data de sincronização do cache tenha decorrido.</span><span class="sxs-lookup"><span data-stu-id="65c9d-134">If the cache synchronization date is set to a future date, the entry is revalidated every time it is requested, until the cache synchronization date passes.</span></span>  
  
 <span data-ttu-id="65c9d-135">Os seguintes tópicos fornecem informações sobre os efeitos da combinação de critérios da política de cache baseada em tempo:</span><span class="sxs-lookup"><span data-stu-id="65c9d-135">The following topics provide information about the effects of combining time-based cache policy criteria:</span></span>  
  
-   [<span data-ttu-id="65c9d-136">Interação da política de cache – idade máxima e desatualização máxima</span><span class="sxs-lookup"><span data-stu-id="65c9d-136">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)  
  
-   [<span data-ttu-id="65c9d-137">Interação da política de cache – idade máxima e atualização mínima</span><span class="sxs-lookup"><span data-stu-id="65c9d-137">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)  
  
## <a name="see-also"></a><span data-ttu-id="65c9d-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="65c9d-138">See Also</span></span>  
 <span data-ttu-id="65c9d-139">[Gerenciamento de cache para aplicativos de rede](../../../docs/framework/network-programming/cache-management-for-network-applications.md) </span><span class="sxs-lookup"><span data-stu-id="65c9d-139">[Cache Management for Network Applications](../../../docs/framework/network-programming/cache-management-for-network-applications.md) </span></span>  
 <span data-ttu-id="65c9d-140">[Política de cache](../../../docs/framework/network-programming/cache-policy.md) </span><span class="sxs-lookup"><span data-stu-id="65c9d-140">[Cache Policy](../../../docs/framework/network-programming/cache-policy.md) </span></span>  
 <span data-ttu-id="65c9d-141">[Políticas de cache baseadas na localização](../../../docs/framework/network-programming/location-based-cache-policies.md) </span><span class="sxs-lookup"><span data-stu-id="65c9d-141">[Location-Based Cache Policies](../../../docs/framework/network-programming/location-based-cache-policies.md) </span></span>  
 <span data-ttu-id="65c9d-142">[Configurando o cache em aplicativos de rede](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md) </span><span class="sxs-lookup"><span data-stu-id="65c9d-142">[Configuring Caching in Network Applications](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md) </span></span>  
 [<span data-ttu-id="65c9d-143">\<Elemento requestCaching> (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="65c9d-143">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)

