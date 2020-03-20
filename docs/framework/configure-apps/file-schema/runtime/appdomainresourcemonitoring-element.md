---
title: Elemento <appDomainResourceMonitoring>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
ms.openlocfilehash: 3c6092b6c34bb13c0ad0e66df2d3b7e65ac3de7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154370"
---
# <a name="appdomainresourcemonitoring-element"></a><span data-ttu-id="2839f-102">\<aplicativoDomínioElemento de>deMonitoramento de recursos</span><span class="sxs-lookup"><span data-stu-id="2839f-102">\<appDomainResourceMonitoring> Element</span></span>
<span data-ttu-id="2839f-103">Instrui o runtime a coletar estatísticas sobre todos os domínios de aplicativos no processo durante toda a vida do processo.</span><span class="sxs-lookup"><span data-stu-id="2839f-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
<span data-ttu-id="2839f-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2839f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2839f-105">&nbsp;&nbsp;[**\<>de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="2839f-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="2839f-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomínioDomínioMonitorando>**</span><span class="sxs-lookup"><span data-stu-id="2839f-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainResourceMonitoring>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2839f-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2839f-107">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2839f-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2839f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2839f-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2839f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2839f-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="2839f-110">Attributes</span></span>  
  
|<span data-ttu-id="2839f-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="2839f-111">Attribute</span></span>|<span data-ttu-id="2839f-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="2839f-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="2839f-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="2839f-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="2839f-114">Especifica se o tempo de execução coleta estatísticas para monitoramento de recursos de domínio de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="2839f-114">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="2839f-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="2839f-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="2839f-116">Valor</span><span class="sxs-lookup"><span data-stu-id="2839f-116">Value</span></span>|<span data-ttu-id="2839f-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="2839f-117">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="2839f-118">Estatísticas para monitoramento de recursos de domínio de aplicativos são coletadas.</span><span class="sxs-lookup"><span data-stu-id="2839f-118">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="2839f-119">As estatísticas para monitoramento de recursos de domínio de aplicativos não são coletadas.</span><span class="sxs-lookup"><span data-stu-id="2839f-119">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2839f-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2839f-120">Child Elements</span></span>  
 <span data-ttu-id="2839f-121">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="2839f-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2839f-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2839f-122">Parent Elements</span></span>  
  
|<span data-ttu-id="2839f-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="2839f-123">Element</span></span>|<span data-ttu-id="2839f-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="2839f-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2839f-125">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2839f-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="2839f-126">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="2839f-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2839f-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="2839f-127">Remarks</span></span>  
 <span data-ttu-id="2839f-128">O monitoramento de recursos de domínio de aplicativos está disponível através da classe de domínio de aplicativo gerenciado, da interface [de hospedagem ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) e do rastreamento de eventos para O Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="2839f-128">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="2839f-129">Quando o monitoramento é ativado, as estatísticas são coletadas para todos os domínios de aplicativos no processo de vida do processo.</span><span class="sxs-lookup"><span data-stu-id="2839f-129">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="2839f-130">Para habilitar o monitoramento a <xref:System.AppDomain.MonitoringIsEnabled%2A> partir do código gerenciado, use a propriedade.</span><span class="sxs-lookup"><span data-stu-id="2839f-130">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="2839f-131">Este elemento de configuração está disponível apenas no .NET Framework 4 e posterior.</span><span class="sxs-lookup"><span data-stu-id="2839f-131">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2839f-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2839f-132">Example</span></span>  
 <span data-ttu-id="2839f-133">O exemplo a seguir mostra como ativar o monitoramento de recursos de domínio de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="2839f-133">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2839f-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="2839f-134">See also</span></span>

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="2839f-135">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="2839f-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2839f-136">Esquema de arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="2839f-136">Configuration File Schema</span></span>](../index.md)
