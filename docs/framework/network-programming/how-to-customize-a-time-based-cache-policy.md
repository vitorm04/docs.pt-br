---
title: Como personalizar uma política de cache com base no tempo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- customizing time-based cache policies
- cache [.NET Framework], time-based policies
ms.assetid: 8d84f936-2376-4356-9264-03162e0f9279
ms.openlocfilehash: 1a2ba404e333eeec2a23758c834876d0df5aba81
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040629"
---
# <a name="how-to-customize-a-time-based-cache-policy"></a><span data-ttu-id="a5778-102">Como personalizar uma política de cache com base no tempo</span><span class="sxs-lookup"><span data-stu-id="a5778-102">How to: customize a time-based cache policy</span></span>

<span data-ttu-id="a5778-103">Ao criar uma política de cache baseada em tempo, você pode personalizar o comportamento do cache especificando valores para a idade máxima, atualização mínima, desatualização máxima ou data de sincronização do cache.</span><span class="sxs-lookup"><span data-stu-id="a5778-103">When creating a time-based cache policy, you can customize caching behavior by specifying values for maximum age, minimum freshness, maximum staleness, or cache synchronization date.</span></span> <span data-ttu-id="a5778-104">O objeto <xref:System.Net.Cache.HttpRequestCachePolicy> fornece vários construtores que permitem especificar combinações válidas desses valores.</span><span class="sxs-lookup"><span data-stu-id="a5778-104">The <xref:System.Net.Cache.HttpRequestCachePolicy> object provides several constructors that allow you to specify valid combinations of these values.</span></span>

## <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a><span data-ttu-id="a5778-105">Para criar uma política de cache baseada em tempo que usa uma data de sincronização do cache</span><span class="sxs-lookup"><span data-stu-id="a5778-105">To create a time-based cache policy that uses a cache synchronization date</span></span>

<span data-ttu-id="a5778-106">Crie uma política de cache baseada em tempo que usa uma data de sincronização de cache passando um objeto <xref:System.DateTime> para o Construtor <xref:System.Net.Cache.HttpRequestCachePolicy>:</span><span class="sxs-lookup"><span data-stu-id="a5778-106">Create a time-based cache policy that uses a cache synchronization date by passing a <xref:System.DateTime> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor:</span></span>

```csharp
public static HttpRequestCachePolicy CreateLastSyncPolicy(DateTime when)
{
    var policy = new HttpRequestCachePolicy(when);
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

<span data-ttu-id="a5778-107">A saída é semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="a5778-107">The output is similar to the following:</span></span>

```output
When: 1/14/2004 8:07:30 AM
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a><span data-ttu-id="a5778-108">Para criar uma política de cache baseada em tempo com base na atualização mínima</span><span class="sxs-lookup"><span data-stu-id="a5778-108">To create a time-based cache policy that is based on minimum freshness</span></span>

<span data-ttu-id="a5778-109">Crie uma política de cache baseada em tempo com base na atualização mínima, especificando <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> como o valor do parâmetro `cacheAgeControl` e passando um objeto <xref:System.TimeSpan> para o Construtor <xref:System.Net.Cache.HttpRequestCachePolicy>:</span><span class="sxs-lookup"><span data-stu-id="a5778-109">Create a time-based cache policy that is based on minimum freshness by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> as the `cacheAgeControl` parameter value and passing a <xref:System.TimeSpan> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor:</span></span>

```csharp
public static HttpRequestCachePolicy CreateMinFreshPolicy(TimeSpan span)
{
    var policy = new HttpRequestCachePolicy(HttpCacheAgeControl.MinFresh, span);
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

<span data-ttu-id="a5778-110">Para a seguinte invocação:</span><span class="sxs-lookup"><span data-stu-id="a5778-110">For the following invocation:</span></span>

```csharp
CreateMinFreshPolicy(new TimeSpan(1,0,0));
```

<span data-ttu-id="a5778-111">A saída é:</span><span class="sxs-lookup"><span data-stu-id="a5778-111">The output is:</span></span>

```output
Level:Default MinFresh:3600
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a><span data-ttu-id="a5778-112">Para criar uma política de cache baseada em tempo com base na atualização mínima e idade máxima</span><span class="sxs-lookup"><span data-stu-id="a5778-112">To create a time-based cache policy that is based on minimum freshness and maximum age</span></span>

<span data-ttu-id="a5778-113">Crie uma política de cache baseada em tempo com base na atualização mínima e na idade máxima especificando <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> como o valor do parâmetro `cacheAgeControl` e passando dois objetos <xref:System.TimeSpan> para o Construtor <xref:System.Net.Cache.HttpRequestCachePolicy>, um para especificar a idade máxima para os recursos e um segundo para Especifique a atualização mínima permitida para um objeto retornado do cache:</span><span class="sxs-lookup"><span data-stu-id="a5778-113">Create a time-based cache policy that is based on minimum freshness and maximum age by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> as the `cacheAgeControl` parameter value and passing two <xref:System.TimeSpan> objects to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor, one to specify the maximum age for resources and a second to specify the minimum freshness permitted for an object returned from the cache:</span></span>

```csharp
public static HttpRequestCachePolicy CreateFreshAndAgePolicy(TimeSpan freshMinimum, TimeSpan ageMaximum)
{
    var policy = new HttpRequestCachePolicy(HttpCacheAgeControl.MaxAgeAndMinFresh, ageMaximum, freshMinimum);
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

<span data-ttu-id="a5778-114">Para a seguinte invocação:</span><span class="sxs-lookup"><span data-stu-id="a5778-114">For the following invocation:</span></span>
  
```csharp
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  

<span data-ttu-id="a5778-115">A saída é:</span><span class="sxs-lookup"><span data-stu-id="a5778-115">The output is:</span></span>
  
```output
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a><span data-ttu-id="a5778-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5778-116">See also</span></span>

- [<span data-ttu-id="a5778-117">Gerenciamento de cache para aplicativos de rede</span><span class="sxs-lookup"><span data-stu-id="a5778-117">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="a5778-118">Política de cache</span><span class="sxs-lookup"><span data-stu-id="a5778-118">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="a5778-119">Políticas de cache baseadas na localização</span><span class="sxs-lookup"><span data-stu-id="a5778-119">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="a5778-120">Políticas de cache baseadas em tempo</span><span class="sxs-lookup"><span data-stu-id="a5778-120">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="a5778-121">\<Elemento requestCaching> (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="a5778-121">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
