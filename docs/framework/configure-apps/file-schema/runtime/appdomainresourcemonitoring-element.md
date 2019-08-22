---
title: Elemento <appDomainResourceMonitoring>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b82be30c18cde361aa412ee1b631c8368c8de1b3
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663923"
---
# <a name="appdomainresourcemonitoring-element"></a><span data-ttu-id="684ea-102">\<Elemento de > appDomainResourceMonitoring</span><span class="sxs-lookup"><span data-stu-id="684ea-102">\<appDomainResourceMonitoring> Element</span></span>
<span data-ttu-id="684ea-103">Instrui o tempo de execução a coletar estatísticas sobre todos os domínios de aplicativos no processo durante toda a vida do processo.</span><span class="sxs-lookup"><span data-stu-id="684ea-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="684ea-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="684ea-104">\<configuration></span></span>  
<span data-ttu-id="684ea-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="684ea-105">\<runtime></span></span>  
<span data-ttu-id="684ea-106">\<appDomainResourceMonitoring></span><span class="sxs-lookup"><span data-stu-id="684ea-106">\<appDomainResourceMonitoring></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="684ea-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="684ea-107">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="684ea-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="684ea-108">Attributes and Elements</span></span>  
 <span data-ttu-id="684ea-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="684ea-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="684ea-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="684ea-110">Attributes</span></span>  
  
|<span data-ttu-id="684ea-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="684ea-111">Attribute</span></span>|<span data-ttu-id="684ea-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="684ea-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="684ea-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="684ea-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="684ea-114">Especifica se o tempo de execução coleta estatísticas para o monitoramento de recursos de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="684ea-114">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="684ea-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="684ea-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="684ea-116">Valor</span><span class="sxs-lookup"><span data-stu-id="684ea-116">Value</span></span>|<span data-ttu-id="684ea-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="684ea-117">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="684ea-118">As estatísticas de monitoramento de recursos de domínio de aplicativo são coletadas.</span><span class="sxs-lookup"><span data-stu-id="684ea-118">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="684ea-119">As estatísticas para o monitoramento de recursos de domínio de aplicativo não são coletadas.</span><span class="sxs-lookup"><span data-stu-id="684ea-119">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="684ea-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="684ea-120">Child Elements</span></span>  
 <span data-ttu-id="684ea-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="684ea-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="684ea-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="684ea-122">Parent Elements</span></span>  
  
|<span data-ttu-id="684ea-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="684ea-123">Element</span></span>|<span data-ttu-id="684ea-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="684ea-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="684ea-125">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="684ea-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="684ea-126">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="684ea-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="684ea-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="684ea-127">Remarks</span></span>  
 <span data-ttu-id="684ea-128">O monitoramento de recursos de domínio de aplicativo está disponível por meio da classe de domínio do aplicativo gerenciado, da interface [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) de hospedagem e do ETW (rastreamento de eventos para Windows).</span><span class="sxs-lookup"><span data-stu-id="684ea-128">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="684ea-129">Quando o monitoramento está habilitado, as estatísticas são coletadas para todos os domínios de aplicativo no processo durante a vida útil do processo.</span><span class="sxs-lookup"><span data-stu-id="684ea-129">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="684ea-130">Para habilitar o monitoramento do código gerenciado, use <xref:System.AppDomain.MonitoringIsEnabled%2A> a propriedade.</span><span class="sxs-lookup"><span data-stu-id="684ea-130">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="684ea-131">Este elemento de configuração está disponível apenas no .NET Framework 4 e posterior.</span><span class="sxs-lookup"><span data-stu-id="684ea-131">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="684ea-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="684ea-132">Example</span></span>  
 <span data-ttu-id="684ea-133">O exemplo a seguir mostra como habilitar o monitoramento de recursos de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="684ea-133">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="684ea-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="684ea-134">See also</span></span>

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="684ea-135">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="684ea-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="684ea-136">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="684ea-136">Configuration File Schema</span></span>](../index.md)
