---
title: Elemento <settings> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
ms.openlocfilehash: ba08f630dc602c950da309bf29482d85b41af7ef
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697691"
---
# <a name="settings-element-network-settings"></a><span data-ttu-id="20ba9-102">\<settings > elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="20ba9-102">\<settings> Element (Network Settings)</span></span>
<span data-ttu-id="20ba9-103">Configura as opções de rede básicaspara o namespace <xref:System.Net?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="20ba9-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  
  
[<span data-ttu-id="20ba9-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="20ba9-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="20ba9-105">&nbsp; @ no__t-1[ **@no__t -4System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="20ba9-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="20ba9-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<settings >**</span><span class="sxs-lookup"><span data-stu-id="20ba9-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<settings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20ba9-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="20ba9-107">Syntax</span></span>  
  
```xml  
<settings>  
  <httpListener>...</httpListener>  
  <httpWebRequest>...</httpWebRequest>  
  <ipv6>...</ipv6>  
  <performanceCounters>...</performanceCounters>  
  <servicePointManager>...</servicePointManager>  
  <socket>...</socket>  
  <webProxyScript>...</webProxyScript>  
</settings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="20ba9-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="20ba9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="20ba9-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="20ba9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20ba9-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="20ba9-110">Attributes</span></span>  
 <span data-ttu-id="20ba9-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="20ba9-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="20ba9-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="20ba9-112">Child Elements</span></span>  
  
|<span data-ttu-id="20ba9-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="20ba9-113">Element</span></span>|<span data-ttu-id="20ba9-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="20ba9-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20ba9-115">httpListener</span><span class="sxs-lookup"><span data-stu-id="20ba9-115">httpListener</span></span>](httplistener-element-network-settings.md)|<span data-ttu-id="20ba9-116">Personaliza os parâmetros usados pela classe <xref:System.Net.HttpListener>.</span><span class="sxs-lookup"><span data-stu-id="20ba9-116">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="20ba9-117">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="20ba9-117">httpWebRequest</span></span>](httpwebrequest-element-network-settings.md)|<span data-ttu-id="20ba9-118">Personaliza os parâmetros de solicitação da Web.</span><span class="sxs-lookup"><span data-stu-id="20ba9-118">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="20ba9-119">ipv6</span><span class="sxs-lookup"><span data-stu-id="20ba9-119">ipv6</span></span>](ipv6-element-network-settings.md)|<span data-ttu-id="20ba9-120">Habilita o suporte a IPv6 (protocolo IP versão 6).</span><span class="sxs-lookup"><span data-stu-id="20ba9-120">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="20ba9-121">\<performanceCounter > elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="20ba9-121">\<performanceCounter> Element (Network Settings)</span></span>](performancecounter-element-network-settings.md)|<span data-ttu-id="20ba9-122">Habilita contadores de desempenho de rede.</span><span class="sxs-lookup"><span data-stu-id="20ba9-122">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="20ba9-123">servicePointManager</span><span class="sxs-lookup"><span data-stu-id="20ba9-123">servicePointManager</span></span>](servicepointmanager-element-network-settings.md)|<span data-ttu-id="20ba9-124">Configura conexões com recursos de rede.</span><span class="sxs-lookup"><span data-stu-id="20ba9-124">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="20ba9-125">socket</span><span class="sxs-lookup"><span data-stu-id="20ba9-125">socket</span></span>](socket-element-network-settings.md)|<span data-ttu-id="20ba9-126">Especifica se as operações de soquete usam portas de conclusão.</span><span class="sxs-lookup"><span data-stu-id="20ba9-126">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="20ba9-127">\<webProxyScript > elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="20ba9-127">\<webProxyScript> Element (Network Settings)</span></span>](webproxyscript-element-network-settings.md)|<span data-ttu-id="20ba9-128">Configura as características do script usado para descobrir proxies da Web.</span><span class="sxs-lookup"><span data-stu-id="20ba9-128">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="20ba9-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="20ba9-129">Parent Elements</span></span>  
  
|<span data-ttu-id="20ba9-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="20ba9-130">Element</span></span>|<span data-ttu-id="20ba9-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="20ba9-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20ba9-132">system.net</span><span class="sxs-lookup"><span data-stu-id="20ba9-132">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="20ba9-133">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="20ba9-133">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20ba9-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="20ba9-134">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="20ba9-135">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="20ba9-135">Configuration Files</span></span>  
 <span data-ttu-id="20ba9-136">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="20ba9-136">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20ba9-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="20ba9-137">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- [<span data-ttu-id="20ba9-138">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="20ba9-138">Network Settings Schema</span></span>](index.md)
