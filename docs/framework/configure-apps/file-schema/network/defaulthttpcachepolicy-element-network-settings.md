---
title: Elemento <defaultHttpCachePolicy> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultHttpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultHttpCachePolicy
helpviewer_keywords:
- defaultHttpCachePolicy element
- <defaultHttpCachePolicy> element
ms.assetid: 2c1247d0-39b0-4c12-919a-a925ce075c79
ms.openlocfilehash: c5029a7d1e53c28d0abb232efdc3e0bd2c9658d4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088412"
---
# <a name="defaulthttpcachepolicy-element-network-settings"></a><span data-ttu-id="30678-102">Elemento \<defaultHttpCachePolicy> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="30678-102">\<defaultHttpCachePolicy> Element (Network Settings)</span></span>
<span data-ttu-id="30678-103">Descreve se o cache HTTP está ativo e descreve a política de cache padrão.</span><span class="sxs-lookup"><span data-stu-id="30678-103">Describes whether HTTP caching is active and describes the default caching policy.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultHttpCachePolicy>**

## <a name="syntax"></a><span data-ttu-id="30678-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="30678-104">Syntax</span></span>  
  
```xml  
<defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss|minValue|maxValue"  
  maximumAge="d.hh:mm:ss|minValue|maxValue"  
  maximumStale="d.hh:mm:ss|minValue|maxValue"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30678-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="30678-105">Attributes and Elements</span></span>  
 <span data-ttu-id="30678-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="30678-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30678-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="30678-107">Attributes</span></span>  
  
|<span data-ttu-id="30678-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="30678-108">Attribute</span></span>|<span data-ttu-id="30678-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="30678-109">Description</span></span>|  
|---------------|-----------------|  
|`maximumAge`|<span data-ttu-id="30678-110">Especifica o intervalo de tempo máximo antes que um objeto armazenado em cache seja marcado como expirado.</span><span class="sxs-lookup"><span data-stu-id="30678-110">Specifies the maximum time interval before a cached object is marked as expired.</span></span>|  
|`maximumStale`|<span data-ttu-id="30678-111">Especifica o tempo máximo após o tempo de atualização computado antes que um objeto armazenado em cache seja marcado como expirado.</span><span class="sxs-lookup"><span data-stu-id="30678-111">Specifies the maximum time past the computed freshness time before a cached object is marked as expired.</span></span>|  
|`minimumFresh`|<span data-ttu-id="30678-112">Especifica o tempo mínimo para um objeto em cache ser considerado atualizado.</span><span class="sxs-lookup"><span data-stu-id="30678-112">Specifies the minimum time for a cached object to be considered fresh.</span></span>|  
|`policyLevel`|<span data-ttu-id="30678-113">Especifica se a política de cache é automática ou se o cache é ignorado.</span><span class="sxs-lookup"><span data-stu-id="30678-113">Specifies whether the caching policy is automatic, or whether the cache is bypassed.</span></span> <span data-ttu-id="30678-114">O valor padrão é `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="30678-114">The default value is `BypassCache`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30678-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="30678-115">Child Elements</span></span>  
 <span data-ttu-id="30678-116">Nenhum</span><span class="sxs-lookup"><span data-stu-id="30678-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="30678-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="30678-117">Parent Elements</span></span>  
  
|<span data-ttu-id="30678-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="30678-118">Element</span></span>|<span data-ttu-id="30678-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="30678-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30678-120">requestCaching</span><span class="sxs-lookup"><span data-stu-id="30678-120">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="30678-121">Controla o mecanismo de cache para solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="30678-121">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30678-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="30678-122">Remarks</span></span>  
 <span data-ttu-id="30678-123">O valor do `policyLevel` atributo é `BypassCache` ou `Default` .</span><span class="sxs-lookup"><span data-stu-id="30678-123">The value for the `policyLevel` attribute is either `BypassCache` or `Default`.</span></span>  
  
 <span data-ttu-id="30678-124">Os valores para `maximumAge` os `maximumStale` elementos, e `minimumFresh` são um intervalo de tempo explícito com um formato de *d*.\* HH*:*mm*:*SS\* (dias, horas, minutos e segundos) ou as constantes `minValue` ou `maxValue` , conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="30678-124">Values for the `maximumAge`, `maximumStale`, and `minimumFresh` elements are either an explicit time interval with a format of *d*.*hh*:*mm*:*ss* (days, hours, minutes, and seconds), or the constants `minValue` or `maxValue`, as appropriate.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="30678-125">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="30678-125">Configuration Files</span></span>  
 <span data-ttu-id="30678-126">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="30678-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="30678-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30678-127">Example</span></span>  
 <span data-ttu-id="30678-128">O exemplo a seguir mostra como especificar uma hora de atualização mínima de seis horas, um tempo de vida máximo de dois dias e um tempo máximo de obsoleto de quatro horas.</span><span class="sxs-lookup"><span data-stu-id="30678-128">The following example shows how to specify a minimum fresh time of six hours, a maximum age time of two days, and a maximum stale time of four hours.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultHttpCachePolicy  
        minimumFresh="0.06:00:00"  
        maximumAge="2.00:00:00"  
        maximumStale="0.04:00:00"
      />  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="30678-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="30678-129">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="30678-130">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="30678-130">Network Settings Schema</span></span>](index.md)
