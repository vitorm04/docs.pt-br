---
title: Elemento <performanceCounters>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
- <performanceCounters> element
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
ms.openlocfilehash: f52fdb2d5b0b7911de63f96663e70735d2f2496c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "71697148"
---
# <a name="performancecounters-element"></a><span data-ttu-id="231a0-102">Elemento \<performanceCounters></span><span class="sxs-lookup"><span data-stu-id="231a0-102">\<performanceCounters> Element</span></span>

<span data-ttu-id="231a0-103">Especifica o tamanho da memória global compartilhada por contadores de desempenho.</span><span class="sxs-lookup"><span data-stu-id="231a0-103">Specifies the size of the global memory shared by performance counters.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**  

## <a name="syntax"></a><span data-ttu-id="231a0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="231a0-104">Syntax</span></span>

```xml
<performanceCounters filemappingsize="524288" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="231a0-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="231a0-105">Attributes and Elements</span></span>

<span data-ttu-id="231a0-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="231a0-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="231a0-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="231a0-107">Attributes</span></span>

|<span data-ttu-id="231a0-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="231a0-108">Attribute</span></span>|<span data-ttu-id="231a0-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="231a0-109">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="231a0-110">filemappingsize</span><span class="sxs-lookup"><span data-stu-id="231a0-110">filemappingsize</span></span>|<span data-ttu-id="231a0-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="231a0-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="231a0-112">Especifica o tamanho, em bytes, da memória global compartilhada pelos contadores de desempenho.</span><span class="sxs-lookup"><span data-stu-id="231a0-112">Specifies the size, in bytes, of the global memory shared by performance counters.</span></span> <span data-ttu-id="231a0-113">O padrão é 524288.</span><span class="sxs-lookup"><span data-stu-id="231a0-113">The default is 524288.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="231a0-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="231a0-114">Child Elements</span></span>

<span data-ttu-id="231a0-115">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="231a0-115">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="231a0-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="231a0-116">Parent Elements</span></span>

|<span data-ttu-id="231a0-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="231a0-117">Element</span></span>|<span data-ttu-id="231a0-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="231a0-118">Description</span></span>|
|-------------|-----------------|
|`Configuration`|<span data-ttu-id="231a0-119">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="231a0-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`system.diagnostics`|<span data-ttu-id="231a0-120">Especifica o elemento raiz para a seção de configuração ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="231a0-120">Specifies the root element for the ASP.NET configuration section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="231a0-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="231a0-121">Remarks</span></span>

<span data-ttu-id="231a0-122">Os contadores de desempenho usam um arquivo mapeado de memória ou memória compartilhada para publicar dados de desempenho.</span><span class="sxs-lookup"><span data-stu-id="231a0-122">Performance counters use a memory mapped file, or shared memory, to publish performance data.</span></span>  <span data-ttu-id="231a0-123">O tamanho da memória compartilhada determina quantas instâncias podem ser usadas de uma vez.</span><span class="sxs-lookup"><span data-stu-id="231a0-123">The size of the shared memory determines how many instances can be used at once.</span></span>  <span data-ttu-id="231a0-124">Há dois tipos de memória compartilhada: memória compartilhada global e memória compartilhada separada.</span><span class="sxs-lookup"><span data-stu-id="231a0-124">There are two types of shared memory: global shared memory and separate shared memory.</span></span>  <span data-ttu-id="231a0-125">A memória compartilhada global é usada por todas as categorias de contador de desempenho instaladas com as versões 1,0 ou 1,1 do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="231a0-125">The global shared memory is used by all performance counter categories installed with the .NET Framework versions 1.0 or 1.1.</span></span>  <span data-ttu-id="231a0-126">As categorias de contador de desempenho instaladas com o .NET Framework versão 2,0 usam memória compartilhada separada, com cada categoria de contador de desempenho com sua própria memória.</span><span class="sxs-lookup"><span data-stu-id="231a0-126">Performance counter categories installed with the .NET Framework version 2.0 use separate shared memory, with each performance counter category having its own memory.</span></span>

<span data-ttu-id="231a0-127">O tamanho da memória compartilhada global só pode ser definido com um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="231a0-127">The size of global shared memory can be set only with a configuration file.</span></span>  <span data-ttu-id="231a0-128">O tamanho padrão é 524.288 bSim, o tamanho máximo é de 33.554.432 bytes e o tamanho mínimo é de 32.768 bytes.</span><span class="sxs-lookup"><span data-stu-id="231a0-128">The default size is 524,288 byes, the maximum size is 33,554,432 bytes, and the minimum size is 32,768 bytes.</span></span>  <span data-ttu-id="231a0-129">Como a memória compartilhada global é compartilhada por todos os processos e categorias, o primeiro criador especifica o tamanho.</span><span class="sxs-lookup"><span data-stu-id="231a0-129">Since the global shared memory is shared by all processes and categories, the first creator specifies the size.</span></span>  <span data-ttu-id="231a0-130">Se você definir o tamanho em seu arquivo de configuração de aplicativo, esse tamanho será usado somente se seu aplicativo for o primeiro aplicativo que faz com que os contadores de desempenho sejam executados.</span><span class="sxs-lookup"><span data-stu-id="231a0-130">If you define the size in your application configuration file, that size is only used if your application is the first application that causes the performance counters to execute.</span></span>  <span data-ttu-id="231a0-131">Portanto, o local correto para especificar o `filemappingsize` valor é o arquivo Machine. config.</span><span class="sxs-lookup"><span data-stu-id="231a0-131">Therefore the correct location to specify the `filemappingsize` value is the Machine.config file.</span></span>  <span data-ttu-id="231a0-132">A memória na memória compartilhada global não pode ser liberada por contadores de desempenho individuais, portanto, eventualmente, a memória compartilhada global será esgotada se um grande número de instâncias de contador de desempenho com nomes diferentes for criado.</span><span class="sxs-lookup"><span data-stu-id="231a0-132">Memory in the global shared memory cannot be released by individual performance counters, so eventually global shared memory is exhausted if a large number of performance counter instances with different names are created.</span></span>

<span data-ttu-id="231a0-133">Para o tamanho da memória compartilhada separada, o valor DWORD FileMappingSize na chave do registro HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\Services \\ *\<category name>* \Performance é referenciado primeiro, seguido pelo valor especificado para a memória compartilhada global no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="231a0-133">For the size of separate shared memory, the DWORD FileMappingSize value in the registry key HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<category name>* \Performance is referenced first, followed by the value specified for the global shared memory in the configuration file.</span></span> <span data-ttu-id="231a0-134">Se o valor de FileMappingSize não existir, o tamanho da memória compartilhada separada será definido como um quarto (1/4) a configuração global no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="231a0-134">If the FileMappingSize value does not exist, then the separate shared memory size is set to one fourth (1/4) the global setting in the configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="231a0-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="231a0-135">See also</span></span>

- <xref:System.Diagnostics.PerformanceCounter>
- <xref:System.Diagnostics.PerformanceCounterCategory>
- <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>
- <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
