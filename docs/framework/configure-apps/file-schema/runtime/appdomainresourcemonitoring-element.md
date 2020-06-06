---
title: Elemento <appDomainResourceMonitoring>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
ms.openlocfilehash: 3c6092b6c34bb13c0ad0e66df2d3b7e65ac3de7e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154370"
---
# <a name="appdomainresourcemonitoring-element"></a><span data-ttu-id="bc084-102">Elemento \<appDomainResourceMonitoring></span><span class="sxs-lookup"><span data-stu-id="bc084-102">\<appDomainResourceMonitoring> Element</span></span>
<span data-ttu-id="bc084-103">Instrui o runtime a coletar estatísticas sobre todos os domínios de aplicativos no processo durante toda a vida do processo.</span><span class="sxs-lookup"><span data-stu-id="bc084-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainResourceMonitoring>**  
  
## <a name="syntax"></a><span data-ttu-id="bc084-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bc084-104">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc084-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bc084-105">Attributes and Elements</span></span>  
 <span data-ttu-id="bc084-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bc084-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc084-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="bc084-107">Attributes</span></span>  
  
|<span data-ttu-id="bc084-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="bc084-108">Attribute</span></span>|<span data-ttu-id="bc084-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="bc084-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="bc084-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="bc084-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="bc084-111">Especifica se o tempo de execução coleta estatísticas para o monitoramento de recursos de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bc084-111">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="bc084-112">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="bc084-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="bc084-113">Valor</span><span class="sxs-lookup"><span data-stu-id="bc084-113">Value</span></span>|<span data-ttu-id="bc084-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="bc084-114">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="bc084-115">As estatísticas de monitoramento de recursos de domínio de aplicativo são coletadas.</span><span class="sxs-lookup"><span data-stu-id="bc084-115">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="bc084-116">As estatísticas para o monitoramento de recursos de domínio de aplicativo não são coletadas.</span><span class="sxs-lookup"><span data-stu-id="bc084-116">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc084-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bc084-117">Child Elements</span></span>  
 <span data-ttu-id="bc084-118">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="bc084-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bc084-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bc084-119">Parent Elements</span></span>  
  
|<span data-ttu-id="bc084-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="bc084-120">Element</span></span>|<span data-ttu-id="bc084-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="bc084-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bc084-122">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bc084-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="bc084-123">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="bc084-123">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc084-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="bc084-124">Remarks</span></span>  
 <span data-ttu-id="bc084-125">O monitoramento de recursos de domínio de aplicativo está disponível por meio da classe de domínio do aplicativo gerenciado, da interface [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) de hospedagem e do ETW (rastreamento de eventos para Windows).</span><span class="sxs-lookup"><span data-stu-id="bc084-125">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="bc084-126">Quando o monitoramento está habilitado, as estatísticas são coletadas para todos os domínios de aplicativo no processo durante a vida útil do processo.</span><span class="sxs-lookup"><span data-stu-id="bc084-126">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="bc084-127">Para habilitar o monitoramento do código gerenciado, use a <xref:System.AppDomain.MonitoringIsEnabled%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="bc084-127">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="bc084-128">Este elemento de configuração está disponível apenas no .NET Framework 4 e posterior.</span><span class="sxs-lookup"><span data-stu-id="bc084-128">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc084-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bc084-129">Example</span></span>  
 <span data-ttu-id="bc084-130">O exemplo a seguir mostra como habilitar o monitoramento de recursos de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bc084-130">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bc084-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="bc084-131">See also</span></span>

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="bc084-132">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="bc084-132">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="bc084-133">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="bc084-133">Configuration File Schema</span></span>](../index.md)
