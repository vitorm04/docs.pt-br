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
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088412"
---
# <a name="defaulthttpcachepolicy-element-network-settings"></a><span data-ttu-id="b86a5-102">\<elemento DefaultHttpCachePolicy > (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="b86a5-102">\<defaultHttpCachePolicy> Element (Network Settings)</span></span>
<span data-ttu-id="b86a5-103">Descreve se o cache HTTP está ativo e descreve a política de cache padrão.</span><span class="sxs-lookup"><span data-stu-id="b86a5-103">Describes whether HTTP caching is active and describes the default caching policy.</span></span>  

<span data-ttu-id="b86a5-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b86a5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b86a5-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="b86a5-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="b86a5-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<requestCaching >** ](requestcaching-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="b86a5-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)</span></span>\
<span data-ttu-id="b86a5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**DefaultHttpCachePolicy >**</span><span class="sxs-lookup"><span data-stu-id="b86a5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultHttpCachePolicy>**</span></span>

## <a name="syntax"></a><span data-ttu-id="b86a5-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b86a5-108">Syntax</span></span>  
  
```xml  
<defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss|minValue|maxValue"  
  maximumAge="d.hh:mm:ss|minValue|maxValue"  
  maximumStale="d.hh:mm:ss|minValue|maxValue"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b86a5-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b86a5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b86a5-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b86a5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b86a5-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="b86a5-111">Attributes</span></span>  
  
|<span data-ttu-id="b86a5-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="b86a5-112">Attribute</span></span>|<span data-ttu-id="b86a5-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="b86a5-113">Description</span></span>|  
|---------------|-----------------|  
|`maximumAge`|<span data-ttu-id="b86a5-114">Especifica o intervalo de tempo máximo antes que um objeto armazenado em cache seja marcado como expirado.</span><span class="sxs-lookup"><span data-stu-id="b86a5-114">Specifies the maximum time interval before a cached object is marked as expired.</span></span>|  
|`maximumStale`|<span data-ttu-id="b86a5-115">Especifica o tempo máximo após o tempo de atualização computado antes que um objeto armazenado em cache seja marcado como expirado.</span><span class="sxs-lookup"><span data-stu-id="b86a5-115">Specifies the maximum time past the computed freshness time before a cached object is marked as expired.</span></span>|  
|`minimumFresh`|<span data-ttu-id="b86a5-116">Especifica o tempo mínimo para um objeto em cache ser considerado atualizado.</span><span class="sxs-lookup"><span data-stu-id="b86a5-116">Specifies the minimum time for a cached object to be considered fresh.</span></span>|  
|`policyLevel`|<span data-ttu-id="b86a5-117">Especifica se a política de cache é automática ou se o cache é ignorado.</span><span class="sxs-lookup"><span data-stu-id="b86a5-117">Specifies whether the caching policy is automatic, or whether the cache is bypassed.</span></span> <span data-ttu-id="b86a5-118">O valor padrão é `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="b86a5-118">The default value is `BypassCache`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b86a5-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b86a5-119">Child Elements</span></span>  
 <span data-ttu-id="b86a5-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="b86a5-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b86a5-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b86a5-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b86a5-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="b86a5-122">Element</span></span>|<span data-ttu-id="b86a5-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="b86a5-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b86a5-124">requestCaching</span><span class="sxs-lookup"><span data-stu-id="b86a5-124">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="b86a5-125">Controla o mecanismo de cache para solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="b86a5-125">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b86a5-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="b86a5-126">Remarks</span></span>  
 <span data-ttu-id="b86a5-127">O valor do atributo `policyLevel` é `BypassCache` ou `Default`.</span><span class="sxs-lookup"><span data-stu-id="b86a5-127">The value for the `policyLevel` attribute is either `BypassCache` or `Default`.</span></span>  
  
 <span data-ttu-id="b86a5-128">Os valores para os elementos `maximumAge`, `maximumStale`e `minimumFresh` são um intervalo de tempo explícito com um formato de *d*. *hh*:*mm*:*SS* (dias, horas, minutos e segundos) ou as constantes `minValue` ou `maxValue`, conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="b86a5-128">Values for the `maximumAge`, `maximumStale`, and `minimumFresh` elements are either an explicit time interval with a format of *d*.*hh*:*mm*:*ss* (days, hours, minutes, and seconds), or the constants `minValue` or `maxValue`, as appropriate.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b86a5-129">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="b86a5-129">Configuration Files</span></span>  
 <span data-ttu-id="b86a5-130">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="b86a5-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b86a5-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b86a5-131">Example</span></span>  
 <span data-ttu-id="b86a5-132">O exemplo a seguir mostra como especificar uma hora de atualização mínima de seis horas, um tempo de vida máximo de dois dias e um tempo máximo de obsoleto de quatro horas.</span><span class="sxs-lookup"><span data-stu-id="b86a5-132">The following example shows how to specify a minimum fresh time of six hours, a maximum age time of two days, and a maximum stale time of four hours.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b86a5-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b86a5-133">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="b86a5-134">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="b86a5-134">Network Settings Schema</span></span>](index.md)
