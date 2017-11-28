---
title: "&lt;configurações&gt; elemento (configurações de rede)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
caps.latest.revision: "21"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 07f356c0425b071ac320e702a9ba7cd6b9537341
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsettingsgt-element-network-settings"></a><span data-ttu-id="655bf-102">&lt;configurações&gt; elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="655bf-102">&lt;settings&gt; Element (Network Settings)</span></span>
<span data-ttu-id="655bf-103">Configura as opções de rede básicaspara o namespace <xref:System.Net?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="655bf-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="655bf-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="655bf-104">\<configuration></span></span>  
<span data-ttu-id="655bf-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="655bf-105">\<system.net></span></span>  
<span data-ttu-id="655bf-106">\<Configurações ></span><span class="sxs-lookup"><span data-stu-id="655bf-106">\<settings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="655bf-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="655bf-107">Syntax</span></span>  
  
```xml  
<settings>  
  <httpListener> … </httpListener>  
  <httpWebRequest> … </httpWebRequest>  
  <ipv6> … </ipv6>  
  <performanceCounters> … </performanceCounters>  
  <servicePointManager> … </servicePointManager>  
  <socket> … </socket>  
  <webProxyScript> … </webProxyScript>  
</settings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="655bf-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="655bf-108">Attributes and Elements</span></span>  
 <span data-ttu-id="655bf-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="655bf-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="655bf-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="655bf-110">Attributes</span></span>  
 <span data-ttu-id="655bf-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="655bf-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="655bf-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="655bf-112">Child Elements</span></span>  
  
|<span data-ttu-id="655bf-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="655bf-113">Element</span></span>|<span data-ttu-id="655bf-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="655bf-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="655bf-115">httpListener</span><span class="sxs-lookup"><span data-stu-id="655bf-115">httpListener</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/httplistener-element-network-settings.md)|<span data-ttu-id="655bf-116">Personaliza os parâmetros usados pelo <xref:System.Net.HttpListener> classe.</span><span class="sxs-lookup"><span data-stu-id="655bf-116">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="655bf-117">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="655bf-117">httpWebRequest</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/httpwebrequest-element-network-settings.md)|<span data-ttu-id="655bf-118">Personaliza os parâmetros de solicitação da Web.</span><span class="sxs-lookup"><span data-stu-id="655bf-118">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="655bf-119">IPv6</span><span class="sxs-lookup"><span data-stu-id="655bf-119">ipv6</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)|<span data-ttu-id="655bf-120">Permite que o protocolo IP versão 6 (IPv6) oferecem suporte.</span><span class="sxs-lookup"><span data-stu-id="655bf-120">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="655bf-121">\<performanceCounter > elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="655bf-121">\<performanceCounter> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/performancecounter-element-network-settings.md)|<span data-ttu-id="655bf-122">Permite que os contadores de desempenho de rede.</span><span class="sxs-lookup"><span data-stu-id="655bf-122">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="655bf-123">servicePointManager</span><span class="sxs-lookup"><span data-stu-id="655bf-123">servicePointManager</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/servicepointmanager-element-network-settings.md)|<span data-ttu-id="655bf-124">Configura conexões aos recursos da rede.</span><span class="sxs-lookup"><span data-stu-id="655bf-124">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="655bf-125">soquete</span><span class="sxs-lookup"><span data-stu-id="655bf-125">socket</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/socket-element-network-settings.md)|<span data-ttu-id="655bf-126">Especifica se as operações de soquete usam portas de conclusão.</span><span class="sxs-lookup"><span data-stu-id="655bf-126">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="655bf-127">\<webProxyScript > elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="655bf-127">\<webProxyScript> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webproxyscript-element-network-settings.md)|<span data-ttu-id="655bf-128">Define as características do script usado para descobrir os proxies da Web.</span><span class="sxs-lookup"><span data-stu-id="655bf-128">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="655bf-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="655bf-129">Parent Elements</span></span>  
  
|<span data-ttu-id="655bf-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="655bf-130">Element</span></span>|<span data-ttu-id="655bf-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="655bf-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="655bf-132">System.NET</span><span class="sxs-lookup"><span data-stu-id="655bf-132">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="655bf-133">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="655bf-133">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="655bf-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="655bf-134">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="655bf-135">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="655bf-135">Configuration Files</span></span>  
 <span data-ttu-id="655bf-136">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="655bf-136">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="655bf-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="655bf-137">See Also</span></span>  
 <xref:System.Net?displayProperty=nameWithType>  
 [<span data-ttu-id="655bf-138">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="655bf-138">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
