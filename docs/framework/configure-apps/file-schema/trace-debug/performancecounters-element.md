---
title: '&lt;performanceCounters&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
- <perfomanceCounters> element
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 69d6deafb6aad88f5d379c7e8d4ac707e4c51815
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47209815"
---
# <a name="ltperformancecountersgt-element"></a><span data-ttu-id="2ce4c-102">&lt;performanceCounters&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="2ce4c-102">&lt;performanceCounters&gt; Element</span></span>
<span data-ttu-id="2ce4c-103">Especifica o tamanho da memória global compartilhada por contadores de desempenho.</span><span class="sxs-lookup"><span data-stu-id="2ce4c-103">Specifies the size of the global memory shared by performance counters.</span></span>  
  
 <span data-ttu-id="2ce4c-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="2ce4c-104">\<configuration></span></span>  
<span data-ttu-id="2ce4c-105">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="2ce4c-105">\<system.diagnostics></span></span>  
<span data-ttu-id="2ce4c-106">\<performanceCounters ></span><span class="sxs-lookup"><span data-stu-id="2ce4c-106">\<performanceCounters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ce4c-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2ce4c-107">Syntax</span></span>  
  
```xml  
<performanceCounters filemappingsize="524288" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2ce4c-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2ce4c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2ce4c-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2ce4c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2ce4c-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="2ce4c-110">Attributes</span></span>  
  
|<span data-ttu-id="2ce4c-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="2ce4c-111">Attribute</span></span>|<span data-ttu-id="2ce4c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="2ce4c-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2ce4c-113">filemappingsize</span><span class="sxs-lookup"><span data-stu-id="2ce4c-113">filemappingsize</span></span>|<span data-ttu-id="2ce4c-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="2ce4c-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="2ce4c-115">Especifica o tamanho, em bytes, da memória global compartilhada pelos contadores de desempenho.</span><span class="sxs-lookup"><span data-stu-id="2ce4c-115">Specifies the size, in bytes, of the global memory shared by performance counters.</span></span> <span data-ttu-id="2ce4c-116">O padrão é 524288.</span><span class="sxs-lookup"><span data-stu-id="2ce4c-116">The default is 524288.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2ce4c-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2ce4c-117">Child Elements</span></span>  
 <span data-ttu-id="2ce4c-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="2ce4c-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2ce4c-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2ce4c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="2ce4c-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="2ce4c-120">Element</span></span>|<span data-ttu-id="2ce4c-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="2ce4c-121">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="2ce4c-122">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2ce4c-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="2ce4c-123">Especifica o elemento raiz para a seção de configuração do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="2ce4c-123">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ce4c-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="2ce4c-124">Remarks</span></span>  
 <span data-ttu-id="2ce4c-125">Contadores de desempenho de usam um arquivo de memória mapeada ou memória compartilhada, para publicar dados de desempenho.</span><span class="sxs-lookup"><span data-stu-id="2ce4c-125">Performance counters use a memory mapped file, or shared memory, to publish performance data.</span></span>  <span data-ttu-id="2ce4c-126">O tamanho da memória compartilhada determina quantas instâncias podem ser usadas ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="2ce4c-126">The size of the shared memory determines how many instances can be used at once.</span></span>  <span data-ttu-id="2ce4c-127">Há dois tipos de memória compartilhada: compartilhado global de memória e memória compartilhada separada.</span><span class="sxs-lookup"><span data-stu-id="2ce4c-127">There are two types of shared memory: global shared memory and separate shared memory.</span></span>  <span data-ttu-id="2ce4c-128">A memória compartilhada global é usada por todas as categorias de contador de desempenho instaladas com o .NET Framework versões 1.0 ou 1.1.</span><span class="sxs-lookup"><span data-stu-id="2ce4c-128">The global shared memory is used by all performance counter categories installed with the .NET Framework versions 1.0 or 1.1.</span></span>  <span data-ttu-id="2ce4c-129">Categorias de contador de desempenho instaladas com o .NET Framework versão 2.0 usam memória compartilhada separada, com cada categoria de contador de desempenho com sua própria memória.</span><span class="sxs-lookup"><span data-stu-id="2ce4c-129">Performance counter categories installed with the .NET Framework version 2.0 use separate shared memory, with each performance counter category having its own memory.</span></span>  
  
 <span data-ttu-id="2ce4c-130">O tamanho da memória compartilhada global pode ser definido somente com um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="2ce4c-130">The size of global shared memory can be set only with a configuration file.</span></span>  <span data-ttu-id="2ce4c-131">O tamanho padrão é 524.288 bytes, o tamanho máximo é 33.554.432 bytes e o tamanho mínimo é 32.768 bytes.</span><span class="sxs-lookup"><span data-stu-id="2ce4c-131">The default size is 524,288 byes, the maximum size is 33,554,432 bytes, and the minimum size is 32,768 bytes.</span></span>  <span data-ttu-id="2ce4c-132">Uma vez que a memória compartilhada global é compartilhada por todos os processos e categorias, o criador do primeiro especifica o tamanho.</span><span class="sxs-lookup"><span data-stu-id="2ce4c-132">Since the global shared memory is shared by all processes and categories, the first creator specifies the size.</span></span>  <span data-ttu-id="2ce4c-133">Se você definir o tamanho em seu arquivo de configuração de aplicativo, esse tamanho só é usado se seu aplicativo é o primeiro aplicativo que faz com que os contadores de desempenho executar.</span><span class="sxs-lookup"><span data-stu-id="2ce4c-133">If you define the size in your application configuration file, that size is only used if your application is the first application that causes the performance counters to execute.</span></span>  <span data-ttu-id="2ce4c-134">Portanto, o local correto para especificar o `filemappingsize` valor é o arquivo Machine. config.</span><span class="sxs-lookup"><span data-stu-id="2ce4c-134">Therefore the correct location to specify the `filemappingsize` value is the Machine.config file.</span></span>  <span data-ttu-id="2ce4c-135">Não é possível liberar a memória na memória global compartilhada por contadores de desempenho individuais, portanto, eventualmente memória compartilhada global é esgotada, se um grande número de instâncias de contador de desempenho com nomes diferentes é criado.</span><span class="sxs-lookup"><span data-stu-id="2ce4c-135">Memory in the global shared memory cannot be released by individual performance counters, so eventually global shared memory is exhausted if a large number of performance counter instances with different names are created.</span></span>  
  
 <span data-ttu-id="2ce4c-136">Para o tamanho da memória compartilhada separada, o valor de DWORD FileMappingSize no registro chave HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<nome da categoria >* \Performance é referenciado primeiro, seguido pelo valor especificado para a memória compartilhada global no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="2ce4c-136">For the size of separate shared memory, the DWORD FileMappingSize value in the registry key HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<category name>* \Performance is referenced first, followed by the value specified for the global shared memory in the configuration file.</span></span> <span data-ttu-id="2ce4c-137">Se o valor de FileMappingSize não existir, o tamanho de memória compartilhada separada é definido como um quarto (1 e 4) a configuração global no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="2ce4c-137">If the FileMappingSize value does not exist, then the separate shared memory size is set to one fourth (1/4) the global setting in the configuration file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ce4c-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2ce4c-138">See Also</span></span>  
 <xref:System.Diagnostics.PerformanceCounter>  
 <xref:System.Diagnostics.PerformanceCounterCategory>  
 <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>  
 <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
