---
title: 'Como: Personalizar uma política de cache baseada em tempo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- customizing time-based cache policies
- cache [.NET Framework], time-based policies
ms.assetid: 8d84f936-2376-4356-9264-03162e0f9279
ms.openlocfilehash: c28c6daf9b873a19291b1636112eae6546412be2
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048322"
---
# <a name="how-to-customize-a-time-based-cache-policy"></a><span data-ttu-id="d8b1b-102">Como: Personalizar uma política de cache baseada em tempo</span><span class="sxs-lookup"><span data-stu-id="d8b1b-102">How to: Customize a Time-Based Cache Policy</span></span>
<span data-ttu-id="d8b1b-103">Ao criar uma política de cache baseada em tempo, você pode personalizar o comportamento do cache especificando valores para a idade máxima, atualização mínima, desatualização máxima ou data de sincronização do cache.</span><span class="sxs-lookup"><span data-stu-id="d8b1b-103">When creating a time-based cache policy, you can customize caching behavior by specifying values for maximum age, minimum freshness, maximum staleness, or cache synchronization date.</span></span> <span data-ttu-id="d8b1b-104">O objeto <xref:System.Net.Cache.HttpRequestCachePolicy> fornece vários construtores que permitem especificar combinações válidas desses valores.</span><span class="sxs-lookup"><span data-stu-id="d8b1b-104">The <xref:System.Net.Cache.HttpRequestCachePolicy> object provides several constructors that allow you to specify valid combinations of these values.</span></span>  
  
### <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a><span data-ttu-id="d8b1b-105">Para criar uma política de cache baseada em tempo que usa uma data de sincronização do cache</span><span class="sxs-lookup"><span data-stu-id="d8b1b-105">To create a time-based cache policy that uses a cache synchronization date</span></span>  
  
- <span data-ttu-id="d8b1b-106">Crie uma política de cache baseada em tempo que usa uma data de sincronização do cache passando um objeto <xref:System.DateTime> para o construtor <xref:System.Net.Cache.HttpRequestCachePolicy>.</span><span class="sxs-lookup"><span data-stu-id="d8b1b-106">Create a time-based cache policy that uses a cache synchronization date by passing a <xref:System.DateTime> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor.</span></span>  
  
    ```csharp  
    public static HttpRequestCachePolicy CreateLastSyncPolicy(DateTime when)  
    {  
        HttpRequestCachePolicy policy =   
            new HttpRequestCachePolicy(when);  
        Console.WriteLine("When: {0}", when);  
        Console.WriteLine(policy.ToString());  
        return policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Function CreateLastSyncPolicy([when] As DateTime) As HttpRequestCachePolicy  
        Dim policy As New HttpRequestCachePolicy([when])  
        Console.WriteLine("When: {0}", [when])  
        Console.WriteLine(policy.ToString())  
        Return policy  
    End Function  
    ```  
  
 <span data-ttu-id="d8b1b-107">A saída é semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="d8b1b-107">The output is similar to the following:</span></span>  
  
```output
When: 1/14/2004 8:07:30 AM  
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a><span data-ttu-id="d8b1b-108">Para criar uma política de cache baseada em tempo com base na atualização mínima</span><span class="sxs-lookup"><span data-stu-id="d8b1b-108">To create a time-based cache policy that is based on minimum freshness</span></span>  
  
- <span data-ttu-id="d8b1b-109">Crie uma política de cache baseada em tempo com base na atualização mínima especificando <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> como o valor de parâmetro `cacheAgeControl` e passando um objeto <xref:System.TimeSpan> para o construtor <xref:System.Net.Cache.HttpRequestCachePolicy>.</span><span class="sxs-lookup"><span data-stu-id="d8b1b-109">Create a time-based cache policy that is based on minimum freshness by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> as the `cacheAgeControl` parameter value and passing a <xref:System.TimeSpan> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor.</span></span>  
  
    ```csharp  
    public static HttpRequestCachePolicy CreateMinFreshPolicy(TimeSpan span)  
    {  
        HttpRequestCachePolicy policy =   
            new HttpRequestCachePolicy(HttpCacheAgeControl.MinFresh, span);  
        Console.WriteLine(policy.ToString());  
        return policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Function CreateMinFreshPolicy(span As TimeSpan) As HttpRequestCachePolicy  
        Dim policy As New HttpRequestCachePolicy(HttpCacheAgeControl.MinFresh, span)  
        Console.WriteLine(policy.ToString())  
        Return policy  
    End Function  
    ```  
  
 <span data-ttu-id="d8b1b-110">Para a seguinte invocação:</span><span class="sxs-lookup"><span data-stu-id="d8b1b-110">For the following invocation:</span></span>  
  
```csharp
CreateMinFreshPolicy(new TimeSpan(1,0,0));  
```  

 <span data-ttu-id="d8b1b-111">A saída é:</span><span class="sxs-lookup"><span data-stu-id="d8b1b-111">The output is:</span></span>
  
```output
Level:Default MinFresh:3600  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a><span data-ttu-id="d8b1b-112">Para criar uma política de cache baseada em tempo com base na atualização mínima e idade máxima</span><span class="sxs-lookup"><span data-stu-id="d8b1b-112">To create a time-based cache policy that is based on minimum freshness and maximum age</span></span>  
  
- <span data-ttu-id="d8b1b-113">Crie uma política de cache baseada em tempo que tem como base a atualização mínima e a idade máxima especificando <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> como o valor do parâmetro `cacheAgeControl` e passando dois objetos <xref:System.TimeSpan> para o construtor <xref:System.Net.Cache.HttpRequestCachePolicy>, um para especificar a idade máxima dos recursos e um segundo para especificar a atualização mínima permitida para um objeto retornado do cache.</span><span class="sxs-lookup"><span data-stu-id="d8b1b-113">Create a time-based cache policy that is based on minimum freshness and maximum age by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> as the `cacheAgeControl` parameter value and passing two <xref:System.TimeSpan> objects to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor, one to specify the maximum age for resources and a second to specify the minimum freshness permitted for an object returned from the cache.</span></span>  
  
    ```csharp  
    public static HttpRequestCachePolicy CreateFreshAndAgePolicy(TimeSpan freshMinimum, TimeSpan ageMaximum)  
    {  
        HttpRequestCachePolicy policy =   
        new HttpRequestCachePolicy(HttpCacheAgeControl.MaxAgeAndMinFresh, ageMaximum, freshMinimum);  
        Console.WriteLine(policy.ToString());  
        return policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Function CreateFreshAndAgePolicy(freshMinimum As TimeSpan, ageMaximum As TimeSpan) As HttpRequestCachePolicy  
        Dim policy As New HttpRequestCachePolicy(HttpCacheAgeControl.MaxAgeAndMinFresh, ageMaximum, freshMinimum)  
        Console.WriteLine(policy.ToString())  
        Return policy  
    End Function  
    ```  
  
 <span data-ttu-id="d8b1b-114">Para a seguinte invocação:</span><span class="sxs-lookup"><span data-stu-id="d8b1b-114">For the following invocation:</span></span>  
  
```csharp
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  

<span data-ttu-id="d8b1b-115">A saída é:</span><span class="sxs-lookup"><span data-stu-id="d8b1b-115">The output is:</span></span>
  
```output
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8b1b-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8b1b-116">See also</span></span>

- [<span data-ttu-id="d8b1b-117">Gerenciamento de cache para aplicativos de rede</span><span class="sxs-lookup"><span data-stu-id="d8b1b-117">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="d8b1b-118">Política de cache</span><span class="sxs-lookup"><span data-stu-id="d8b1b-118">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="d8b1b-119">Políticas de cache baseadas na localização</span><span class="sxs-lookup"><span data-stu-id="d8b1b-119">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="d8b1b-120">Políticas de cache baseadas em tempo</span><span class="sxs-lookup"><span data-stu-id="d8b1b-120">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- <span data-ttu-id="d8b1b-121">[\<requestCaching> Element (Network Settings)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md) [Elemento requestCaching> (configurações de rede)]</span><span class="sxs-lookup"><span data-stu-id="d8b1b-121">[\<requestCaching> Element (Network Settings)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)</span></span>
