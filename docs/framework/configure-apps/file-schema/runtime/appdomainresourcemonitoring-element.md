---
title: Elemento <appDomainResourceMonitoring>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
ms.openlocfilehash: 9ecf2e382b5d483377df871835793219b3f74760
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170266"
---
# <a name="appdomainresourcemonitoring-element"></a><span data-ttu-id="386ec-102">Elemento \<appDomainResourceMonitoring></span><span class="sxs-lookup"><span data-stu-id="386ec-102">\<appDomainResourceMonitoring> Element</span></span>

<span data-ttu-id="386ec-103">Instrui o runtime a coletar estatísticas sobre todos os domínios de aplicativos no processo durante toda a vida do processo.</span><span class="sxs-lookup"><span data-stu-id="386ec-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainResourceMonitoring>**  
  
## <a name="syntax"></a><span data-ttu-id="386ec-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="386ec-104">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="386ec-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="386ec-105">Attributes and Elements</span></span>  

 <span data-ttu-id="386ec-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="386ec-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="386ec-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="386ec-107">Attributes</span></span>  
  
|<span data-ttu-id="386ec-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="386ec-108">Attribute</span></span>|<span data-ttu-id="386ec-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="386ec-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="386ec-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="386ec-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="386ec-111">Especifica se o tempo de execução coleta estatísticas para o monitoramento de recursos de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="386ec-111">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="386ec-112">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="386ec-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="386ec-113">Valor</span><span class="sxs-lookup"><span data-stu-id="386ec-113">Value</span></span>|<span data-ttu-id="386ec-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="386ec-114">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="386ec-115">As estatísticas de monitoramento de recursos de domínio de aplicativo são coletadas.</span><span class="sxs-lookup"><span data-stu-id="386ec-115">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="386ec-116">As estatísticas para o monitoramento de recursos de domínio de aplicativo não são coletadas.</span><span class="sxs-lookup"><span data-stu-id="386ec-116">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="386ec-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="386ec-117">Child Elements</span></span>  

 <span data-ttu-id="386ec-118">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="386ec-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="386ec-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="386ec-119">Parent Elements</span></span>  
  
|<span data-ttu-id="386ec-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="386ec-120">Element</span></span>|<span data-ttu-id="386ec-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="386ec-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="386ec-122">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="386ec-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="386ec-123">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="386ec-123">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="386ec-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="386ec-124">Remarks</span></span>  

 <span data-ttu-id="386ec-125">O monitoramento de recursos de domínio de aplicativo está disponível por meio da classe de domínio do aplicativo gerenciado, da interface [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) de hospedagem e do ETW (rastreamento de eventos para Windows).</span><span class="sxs-lookup"><span data-stu-id="386ec-125">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="386ec-126">Quando o monitoramento está habilitado, as estatísticas são coletadas para todos os domínios de aplicativo no processo durante a vida útil do processo.</span><span class="sxs-lookup"><span data-stu-id="386ec-126">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="386ec-127">Para habilitar o monitoramento do código gerenciado, use a <xref:System.AppDomain.MonitoringIsEnabled%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="386ec-127">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="386ec-128">Este elemento de configuração está disponível apenas no .NET Framework 4 e posterior.</span><span class="sxs-lookup"><span data-stu-id="386ec-128">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="386ec-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="386ec-129">Example</span></span>  

 <span data-ttu-id="386ec-130">O exemplo a seguir mostra como habilitar o monitoramento de recursos de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="386ec-130">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="386ec-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="386ec-131">See also</span></span>

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="386ec-132">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="386ec-132">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="386ec-133">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="386ec-133">Configuration File Schema</span></span>](../index.md)
