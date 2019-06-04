---
title: Elemento <appDomainResourceMonitoring>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad0ae023215eeb1f42f9351369ee77d41d537b88
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487734"
---
# <a name="appdomainresourcemonitoring-element"></a><span data-ttu-id="cefff-102">\<appDomainResourceMonitoring > elemento</span><span class="sxs-lookup"><span data-stu-id="cefff-102">\<appDomainResourceMonitoring> Element</span></span>
<span data-ttu-id="cefff-103">Instrui o tempo de execução a coletar estatísticas sobre todos os domínios de aplicativos no processo durante toda a vida do processo.</span><span class="sxs-lookup"><span data-stu-id="cefff-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="cefff-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="cefff-104">\<configuration></span></span>  
<span data-ttu-id="cefff-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="cefff-105">\<runtime></span></span>  
<span data-ttu-id="cefff-106">\<appDomainResourceMonitoring></span><span class="sxs-lookup"><span data-stu-id="cefff-106">\<appDomainResourceMonitoring></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cefff-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cefff-107">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cefff-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cefff-108">Attributes and Elements</span></span>  
 <span data-ttu-id="cefff-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cefff-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cefff-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="cefff-110">Attributes</span></span>  
  
|<span data-ttu-id="cefff-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="cefff-111">Attribute</span></span>|<span data-ttu-id="cefff-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="cefff-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="cefff-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="cefff-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="cefff-114">Especifica se o tempo de execução de coleta de estatísticas para monitoramento de recursos de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cefff-114">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="cefff-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="cefff-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="cefff-116">Valor</span><span class="sxs-lookup"><span data-stu-id="cefff-116">Value</span></span>|<span data-ttu-id="cefff-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="cefff-117">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="cefff-118">Estatísticas de monitoramento de recursos de domínio do aplicativo serão coletadas.</span><span class="sxs-lookup"><span data-stu-id="cefff-118">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="cefff-119">Estatísticas de monitoramento de recursos de domínio do aplicativo não serão coletadas.</span><span class="sxs-lookup"><span data-stu-id="cefff-119">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cefff-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cefff-120">Child Elements</span></span>  
 <span data-ttu-id="cefff-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="cefff-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cefff-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cefff-122">Parent Elements</span></span>  
  
|<span data-ttu-id="cefff-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="cefff-123">Element</span></span>|<span data-ttu-id="cefff-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="cefff-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="cefff-125">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cefff-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="cefff-126">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="cefff-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cefff-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="cefff-127">Remarks</span></span>  
 <span data-ttu-id="cefff-128">Monitoramento de recursos de domínio do aplicativo está disponível por meio da classe de domínio de aplicativo gerenciado, a hospedagem [ICLRAppDomainResourceMonitor](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface e o rastreamento de eventos para Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="cefff-128">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="cefff-129">Quando o monitoramento é habilitado, as estatísticas são coletadas para todos os domínios de aplicativo no processo durante a vida útil do processo.</span><span class="sxs-lookup"><span data-stu-id="cefff-129">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="cefff-130">Para habilitar o monitoramento do código gerenciado, use o <xref:System.AppDomain.MonitoringIsEnabled%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="cefff-130">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="cefff-131">Este elemento de configuração está disponível apenas no .NET Framework 4 e posterior.</span><span class="sxs-lookup"><span data-stu-id="cefff-131">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cefff-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cefff-132">Example</span></span>  
 <span data-ttu-id="cefff-133">O exemplo a seguir mostra como habilitar o monitoramento de recursos de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cefff-133">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cefff-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cefff-134">See also</span></span>

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="cefff-135">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="cefff-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="cefff-136">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="cefff-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
