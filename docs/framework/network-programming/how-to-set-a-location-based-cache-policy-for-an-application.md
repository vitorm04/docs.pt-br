---
title: 'Como: Definir uma política de cache baseada na localização para um aplicativo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- expliciting defining cache behavior
- location-based cache policies
- local cache
- request cache policies
- cache [.NET Framework], location-based policies
ms.assetid: 683bb88e-3411-4f46-9686-3411b6ba511c
ms.openlocfilehash: 06d458828c77f61e03d18f635ec00f6a7267bab8
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59341862"
---
# <a name="how-to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="f77a8-102">Como: Definir uma política de cache baseada na localização para um aplicativo</span><span class="sxs-lookup"><span data-stu-id="f77a8-102">How to: Set a Location-Based Cache Policy for an Application</span></span>
<span data-ttu-id="f77a8-103">Políticas de cache com base no local permitem que um aplicativo defina explicitamente o comportamento do cache com base na localização do recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="f77a8-103">Location-based cache policies allow an application to explicitly define caching behavior based on the location of the requested resource.</span></span> <span data-ttu-id="f77a8-104">Este tópico demonstra como definir a política de cache programaticamente.</span><span class="sxs-lookup"><span data-stu-id="f77a8-104">This topic demonstrates setting the cache policy programmatically.</span></span> <span data-ttu-id="f77a8-105">Para obter informações sobre como configurar a política para um aplicativo usando os arquivos de configuração, veja o [elemento \<requestCaching> (configurações de rede)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="f77a8-105">For information on setting the policy for an application using the configuration files, see [\<requestCaching> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span></span>  
  
### <a name="to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="f77a8-106">Para definir uma política de cache baseada na localização para um aplicativo</span><span class="sxs-lookup"><span data-stu-id="f77a8-106">To set a location-based cache policy for an application</span></span>  
  
1. <span data-ttu-id="f77a8-107">Crie um objeto <xref:System.Net.Cache.RequestCachePolicy> ou <xref:System.Net.Cache.HttpRequestCachePolicy>.</span><span class="sxs-lookup"><span data-stu-id="f77a8-107">Create a <xref:System.Net.Cache.RequestCachePolicy> or <xref:System.Net.Cache.HttpRequestCachePolicy> object.</span></span>  
  
2. <span data-ttu-id="f77a8-108">Defina o objeto de política como o padrão para o domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f77a8-108">Set the policy object as the default for the application domain.</span></span>  
  
### <a name="to-set-a-policy-that-takes-requested-resources-from-a-cache"></a><span data-ttu-id="f77a8-109">Para definir uma política que toma recursos solicitados de um cache</span><span class="sxs-lookup"><span data-stu-id="f77a8-109">To set a policy that takes requested resources from a cache</span></span>  
  
-   <span data-ttu-id="f77a8-110">Crie uma política que toma recursos solicitados de um cache se disponíveis e, caso contrário, envia solicitações ao servidor, definindo o nível de cache para <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>.</span><span class="sxs-lookup"><span data-stu-id="f77a8-110">Create a policy that takes requested resources from a cache if available, and otherwise, sends requests to the server, by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>.</span></span> <span data-ttu-id="f77a8-111">Uma solicitação pode ser atendida por qualquer cache entre o cliente e servidor, incluindo caches remotos.</span><span class="sxs-lookup"><span data-stu-id="f77a8-111">A request can be fulfilled by any cache between the client and server, including remote caches.</span></span>  
  
    ```csharp  
    public static void UseCacheIfAvailable()  
    {  
        HttpRequestCachePolicy policy = new HttpRequestCachePolicy  
            (HttpRequestCacheLevel.CacheIfAvailable);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub UseCacheIfAvailable()  
        Dim policy As New HttpRequestCachePolicy _  
             (HttpRequestCacheLevel.CacheIfAvailable)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-resources"></a><span data-ttu-id="f77a8-112">Para definir uma política que impede qualquer cache de fornecer recursos</span><span class="sxs-lookup"><span data-stu-id="f77a8-112">To set a policy that prevents any cache from supplying resources</span></span>  
  
-   <span data-ttu-id="f77a8-113">Crie uma política que impede que qualquer cache forneça recursos solicitados, definindo o nível de cache para <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>.</span><span class="sxs-lookup"><span data-stu-id="f77a8-113">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>.</span></span> <span data-ttu-id="f77a8-114">Esse nível de política remove o recurso do cache local se ele está presente e indica para caches remotos que eles também devem remover o recurso.</span><span class="sxs-lookup"><span data-stu-id="f77a8-114">This policy level removes the resource from the local cache if it is present and indicates to remote caches that they should also remove the resource.</span></span>  
  
    ```csharp  
    public static void DoNotUseCache()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy   
            (HttpRequestCacheLevel.NoCacheNoStore);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub DoNotUseCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.NoCacheNoStore)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-returns-requested-resources-only-if-they-are-in-the-local-cache"></a><span data-ttu-id="f77a8-115">Para definir uma política que retorna os recursos solicitados apenas se eles estiverem no cache local</span><span class="sxs-lookup"><span data-stu-id="f77a8-115">To set a policy that returns requested resources only if they are in the local cache</span></span>  
  
-   <span data-ttu-id="f77a8-116">Criar uma política que retorna os recursos solicitados apenas se estiverem no cache local, definindo o nível de cache para <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>.</span><span class="sxs-lookup"><span data-stu-id="f77a8-116">Create a policy that returns requested resources only if they are in the local cache by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>.</span></span> <span data-ttu-id="f77a8-117">Se o recurso solicitado não estiver no cache, uma exceção <xref:System.Net.WebException> será lançada.</span><span class="sxs-lookup"><span data-stu-id="f77a8-117">If the requested resource is not in the cache, a <xref:System.Net.WebException> exception is thrown.</span></span>  
  
    ```csharp  
    public static void OnlyUseCache()  
    {  
        HttpRequestCachePolicy policy = new HttpRequestCachePolicy   
            (HttpRequestCacheLevel.CacheOnly);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub OnlyUseCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.CacheOnly)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-the-local-cache-from-supplying-resources"></a><span data-ttu-id="f77a8-118">Para definir uma política que impede o cache local de fornecer recursos</span><span class="sxs-lookup"><span data-stu-id="f77a8-118">To set a policy that prevents the local cache from supplying resources</span></span>  
  
-   <span data-ttu-id="f77a8-119">Crie uma política que impede que o cache local forneça os recursos solicitados, definindo o nível de cache para <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>.</span><span class="sxs-lookup"><span data-stu-id="f77a8-119">Create a policy that prevents the local cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>.</span></span> <span data-ttu-id="f77a8-120">Se o recurso solicitado está em um cache intermediário e é revalidado com êxito, o cache intermediário pode fornecer o recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="f77a8-120">If the requested resource is in an intermediate cache and is successfully revalidated, the intermediate cache can supply the requested resource.</span></span>  
  
    ```csharp  
    public static void DoNotUseLocalCache()  
    {  
     HttpRequestCachePolicy policy = new HttpRequestCachePolicy   
            (HttpRequestCacheLevel.Refresh);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub DoNotUseLocalCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Refresh)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-requested-resources"></a><span data-ttu-id="f77a8-121">Para definir uma política que impede qualquer cache de fornecer recursos solicitados</span><span class="sxs-lookup"><span data-stu-id="f77a8-121">To set a policy that prevents any cache from supplying requested resources</span></span>  
  
-   <span data-ttu-id="f77a8-122">Crie uma política que impede que qualquer cache forneça recursos solicitados, definindo o nível de cache para <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>.</span><span class="sxs-lookup"><span data-stu-id="f77a8-122">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>.</span></span> <span data-ttu-id="f77a8-123">O recurso retornado pelo servidor pode ser armazenado no cache.</span><span class="sxs-lookup"><span data-stu-id="f77a8-123">The resource returned by the server can be stored in the cache.</span></span>  
  
    ```csharp  
    public static void SendToServer()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy   
            (HttpRequestCacheLevel.Reload);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub SendToServer()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Reload)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-allows-any-cache-to-supply-requested-resources-if-the-resource-on-the-server-is-not-newer-than-the-cached-copy"></a><span data-ttu-id="f77a8-124">Para definir uma política que permite que qualquer cache forneça recursos solicitados se o recurso no servidor não é mais recente do que a cópia armazenada em cache</span><span class="sxs-lookup"><span data-stu-id="f77a8-124">To set a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy</span></span>  
  
-   <span data-ttu-id="f77a8-125">Crie uma política que permite que qualquer cache forneça recursos solicitados se o recurso no servidor não é mais recente do que a cópia armazenada em cache definindo o nível de cache para <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.</span><span class="sxs-lookup"><span data-stu-id="f77a8-125">Create a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.</span></span>  
  
    ```csharp  
    public static void CheckServer()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy  
             (HttpRequestCacheLevel.Revalidate);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub CheckServer()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Revalidate)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f77a8-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f77a8-126">See also</span></span>

- [<span data-ttu-id="f77a8-127">Gerenciamento de cache para aplicativos de rede</span><span class="sxs-lookup"><span data-stu-id="f77a8-127">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [<span data-ttu-id="f77a8-128">Política de cache</span><span class="sxs-lookup"><span data-stu-id="f77a8-128">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)
- [<span data-ttu-id="f77a8-129">Políticas de cache baseadas na localização</span><span class="sxs-lookup"><span data-stu-id="f77a8-129">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [<span data-ttu-id="f77a8-130">Políticas de cache baseadas em tempo</span><span class="sxs-lookup"><span data-stu-id="f77a8-130">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [<span data-ttu-id="f77a8-131">\<Elemento requestCaching> (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="f77a8-131">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
