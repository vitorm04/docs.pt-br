---
title: Elemento <performanceCounter> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounter element
- <performanceCounter> element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
ms.openlocfilehash: 4859f3a9e6de4f1bf8a56212bfe01f94d66f5650
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190235"
---
# <a name="performancecounter-element-network-settings"></a><span data-ttu-id="05bf0-102">Elemento \<performanceCounter> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="05bf0-102">\<performanceCounter> Element (Network Settings)</span></span>

<span data-ttu-id="05bf0-103">Habilita ou desabilita os contadores de desempenho de rede.</span><span class="sxs-lookup"><span data-stu-id="05bf0-103">Enables or disables networking performance counters.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**

## <a name="syntax"></a><span data-ttu-id="05bf0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="05bf0-104">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05bf0-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="05bf0-105">Attributes and Elements</span></span>  

 <span data-ttu-id="05bf0-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="05bf0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05bf0-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="05bf0-107">Attributes</span></span>  
  
|<span data-ttu-id="05bf0-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="05bf0-108">Attribute</span></span>|<span data-ttu-id="05bf0-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="05bf0-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="05bf0-110">Especifica se os contadores de desempenho de rede estão habilitados.</span><span class="sxs-lookup"><span data-stu-id="05bf0-110">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="05bf0-111">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="05bf0-111">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="05bf0-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="05bf0-112">Child Elements</span></span>  

 <span data-ttu-id="05bf0-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="05bf0-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="05bf0-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="05bf0-114">Parent Elements</span></span>  
  
|<span data-ttu-id="05bf0-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="05bf0-115">Element</span></span>|<span data-ttu-id="05bf0-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="05bf0-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05bf0-117">configurações</span><span class="sxs-lookup"><span data-stu-id="05bf0-117">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="05bf0-118">Configura as opções de rede básicaspara o namespace <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="05bf0-118">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05bf0-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="05bf0-119">Remarks</span></span>  

 <span data-ttu-id="05bf0-120">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="05bf0-120">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="05bf0-121">Contadores de desempenho de rede precisam ser habilitados no arquivo de configuração a ser usado.</span><span class="sxs-lookup"><span data-stu-id="05bf0-121">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="05bf0-122">Todos os contadores de desempenho de rede são habilitados ou desabilitados com uma única configuração no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="05bf0-122">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="05bf0-123">Contadores de desempenho de rede individuais não podem ser habilitados nem desabilitados.</span><span class="sxs-lookup"><span data-stu-id="05bf0-123">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="05bf0-124">Para obter mais informações sobre os contadores de desempenho de rede específicos, consulte [Network Performance Counters](../../../debug-trace-profile/performance-counters.md#networking-performance-counters).</span><span class="sxs-lookup"><span data-stu-id="05bf0-124">For more information on the specific networking performance counters, see [Networking performance counters](../../../debug-trace-profile/performance-counters.md#networking-performance-counters).</span></span>  
  
 <span data-ttu-id="05bf0-125">O valor padrão é que os contadores de desempenho de rede estão desabilitados.</span><span class="sxs-lookup"><span data-stu-id="05bf0-125">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="05bf0-126">A <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> propriedade pode ser usada para obter o valor atual do atributo **habilitado** dos arquivos de configuração aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="05bf0-126">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05bf0-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05bf0-127">Example</span></span>  

 <span data-ttu-id="05bf0-128">O exemplo a seguir mostra como configurar o <xref:System.Net> e os namespaces relacionados para habilitar os contadores de desempenho de rede.</span><span class="sxs-lookup"><span data-stu-id="05bf0-128">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="05bf0-129">Veja também</span><span class="sxs-lookup"><span data-stu-id="05bf0-129">See also</span></span>

- <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="05bf0-130">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="05bf0-130">Network Settings Schema</span></span>](index.md)
- [<span data-ttu-id="05bf0-131">Contadores de desempenho de rede</span><span class="sxs-lookup"><span data-stu-id="05bf0-131">Networking Performance Counters</span></span>](../../../debug-trace-profile/performance-counters.md#networking-performance-counters)
