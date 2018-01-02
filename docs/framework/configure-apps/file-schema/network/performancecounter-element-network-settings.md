---
title: "&lt;performanceCounter&gt; elemento (configurações de rede)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounter element
- <performanceCounter> element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 669811b20fd9980b6876683ec7eff4c235a676ef
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltperformancecountergt-element-network-settings"></a><span data-ttu-id="221df-102">&lt;performanceCounter&gt; elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="221df-102">&lt;performanceCounter&gt; Element (Network Settings)</span></span>
<span data-ttu-id="221df-103">Habilita ou desabilita os contadores de desempenho de rede.</span><span class="sxs-lookup"><span data-stu-id="221df-103">Enables or disables networking performance counters.</span></span>  
  
 <span data-ttu-id="221df-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="221df-104">\<configuration></span></span>  
<span data-ttu-id="221df-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="221df-105">\<system.net></span></span>  
<span data-ttu-id="221df-106">\<Configurações ></span><span class="sxs-lookup"><span data-stu-id="221df-106">\<settings></span></span>  
<span data-ttu-id="221df-107">\<performanceCounters ></span><span class="sxs-lookup"><span data-stu-id="221df-107">\<performanceCounters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="221df-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="221df-108">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="221df-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="221df-109">Attributes and Elements</span></span>  
 <span data-ttu-id="221df-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="221df-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="221df-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="221df-111">Attributes</span></span>  
  
|<span data-ttu-id="221df-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="221df-112">Attribute</span></span>|<span data-ttu-id="221df-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="221df-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="221df-114">Especifica se os contadores de desempenho de rede estão habilitados.</span><span class="sxs-lookup"><span data-stu-id="221df-114">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="221df-115">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="221df-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="221df-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="221df-116">Child Elements</span></span>  
 <span data-ttu-id="221df-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="221df-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="221df-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="221df-118">Parent Elements</span></span>  
  
|<span data-ttu-id="221df-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="221df-119">Element</span></span>|<span data-ttu-id="221df-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="221df-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="221df-121">Configurações</span><span class="sxs-lookup"><span data-stu-id="221df-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="221df-122">Configura as opções de rede básicaspara o namespace <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="221df-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="221df-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="221df-123">Remarks</span></span>  
 <span data-ttu-id="221df-124">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="221df-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="221df-125">Contadores de desempenho de rede precisam ser habilitados no arquivo de configuração a ser usado.</span><span class="sxs-lookup"><span data-stu-id="221df-125">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="221df-126">Todos os contadores de desempenho de rede são habilitados ou desabilitados com uma única configuração no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="221df-126">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="221df-127">Contadores de desempenho de rede individuais não podem ser habilitados nem desabilitados.</span><span class="sxs-lookup"><span data-stu-id="221df-127">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="221df-128">Para obter mais informações sobre os contadores de desempenho de rede específicos, consulte [contadores de desempenho de rede](http://msdn.microsoft.com/en-us/d1860235-f643-46ae-846c-ff0ed8b0e3cd).</span><span class="sxs-lookup"><span data-stu-id="221df-128">For more information on the specific networking performance counters, see [Networking Performance Counters](http://msdn.microsoft.com/en-us/d1860235-f643-46ae-846c-ff0ed8b0e3cd).</span></span>  
  
 <span data-ttu-id="221df-129">O valor padrão é que o desempenho do sistema de rede contadores estão desabilitados.</span><span class="sxs-lookup"><span data-stu-id="221df-129">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="221df-130">O <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> propriedade pode ser usada para obter o valor atual do **habilitado** atributo dos arquivos de configuração aplicável.</span><span class="sxs-lookup"><span data-stu-id="221df-130">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="221df-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="221df-131">Example</span></span>  
 <span data-ttu-id="221df-132">O exemplo a seguir mostra como configurar o <xref:System.Net> e relacionados namespaces para habilitar os contadores de desempenho de rede.</span><span class="sxs-lookup"><span data-stu-id="221df-132">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <performanceCounters  
        enabled="true"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="221df-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="221df-133">See Also</span></span>  
 <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="221df-134">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="221df-134">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [<span data-ttu-id="221df-135">Contadores de desempenho de rede</span><span class="sxs-lookup"><span data-stu-id="221df-135">Networking Performance Counters</span></span>](http://msdn.microsoft.com/en-us/d1860235-f643-46ae-846c-ff0ed8b0e3cd)
