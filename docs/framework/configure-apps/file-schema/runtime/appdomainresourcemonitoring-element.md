---
title: Elemento <appDomainResourceMonitoring>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d085fe8b9cf11e2f195468a93b3fa9b3f0817503
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55286553"
---
# <a name="appdomainresourcemonitoring-element"></a><span data-ttu-id="d8087-102">\<appDomainResourceMonitoring > elemento</span><span class="sxs-lookup"><span data-stu-id="d8087-102">\<appDomainResourceMonitoring> Element</span></span>
<span data-ttu-id="d8087-103">Instrui o tempo de execução a coletar estatísticas sobre todos os domínios de aplicativos no processo durante toda a vida do processo.</span><span class="sxs-lookup"><span data-stu-id="d8087-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="d8087-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d8087-104">\<configuration></span></span>  
<span data-ttu-id="d8087-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="d8087-105">\<runtime></span></span>  
<span data-ttu-id="d8087-106">\<appDomainResourceMonitoring></span><span class="sxs-lookup"><span data-stu-id="d8087-106">\<appDomainResourceMonitoring></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8087-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d8087-107">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8087-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d8087-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d8087-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d8087-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8087-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="d8087-110">Attributes</span></span>  
  
|<span data-ttu-id="d8087-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="d8087-111">Attribute</span></span>|<span data-ttu-id="d8087-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="d8087-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="d8087-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="d8087-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="d8087-114">Especifica se o tempo de execução de coleta de estatísticas para monitoramento de recursos de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d8087-114">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d8087-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="d8087-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="d8087-116">Valor</span><span class="sxs-lookup"><span data-stu-id="d8087-116">Value</span></span>|<span data-ttu-id="d8087-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="d8087-117">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="d8087-118">Estatísticas de monitoramento de recursos de domínio do aplicativo serão coletadas.</span><span class="sxs-lookup"><span data-stu-id="d8087-118">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="d8087-119">Estatísticas de monitoramento de recursos de domínio do aplicativo não serão coletadas.</span><span class="sxs-lookup"><span data-stu-id="d8087-119">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d8087-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d8087-120">Child Elements</span></span>  
 <span data-ttu-id="d8087-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d8087-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d8087-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d8087-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d8087-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="d8087-123">Element</span></span>|<span data-ttu-id="d8087-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="d8087-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d8087-125">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d8087-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d8087-126">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="d8087-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8087-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="d8087-127">Remarks</span></span>  
 <span data-ttu-id="d8087-128">Monitoramento de recursos de domínio do aplicativo está disponível por meio da classe de domínio de aplicativo gerenciado, a hospedagem [ICLRAppDomainResourceMonitor](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface e o rastreamento de eventos para Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="d8087-128">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="d8087-129">Quando o monitoramento é habilitado, as estatísticas são coletadas para todos os domínios de aplicativo no processo durante a vida útil do processo.</span><span class="sxs-lookup"><span data-stu-id="d8087-129">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="d8087-130">Para habilitar o monitoramento do código gerenciado, use o <xref:System.AppDomain.MonitoringIsEnabled%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="d8087-130">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="d8087-131">Este elemento de configuração está disponível apenas no [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="d8087-131">This configuration element is available only in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8087-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d8087-132">Example</span></span>  
 <span data-ttu-id="d8087-133">O exemplo a seguir mostra como habilitar o monitoramento de recursos de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d8087-133">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8087-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8087-134">See also</span></span>
- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="d8087-135">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="d8087-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="d8087-136">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="d8087-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
