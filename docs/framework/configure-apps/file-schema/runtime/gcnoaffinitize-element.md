---
title: Elemento GCNoAffinitize
ms.date: 11/08/2019
helpviewer_keywords:
- gcNoAffinitize element
- <gcNoAffinitize> element
ms.openlocfilehash: 4031ff19131c905072696837d1622dbb6e54ae61
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978371"
---
# <a name="gcnoaffinitize-element"></a><span data-ttu-id="ccd43-102">\<elemento de > GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="ccd43-102">\<GCNoAffinitize> element</span></span>

<span data-ttu-id="ccd43-103">Especifica se os threads GC do servidor relacionar ou não devem ser usados com CPUs.</span><span class="sxs-lookup"><span data-stu-id="ccd43-103">Specifies whether or not to affinitize server GC threads with CPUs.</span></span>

<span data-ttu-id="ccd43-104">> de configuração do \<</span><span class="sxs-lookup"><span data-stu-id="ccd43-104">\<configuration></span></span>\
<span data-ttu-id="ccd43-105">> &nbsp;de \<de tempo de execução do &nbsp;</span><span class="sxs-lookup"><span data-stu-id="ccd43-105">&nbsp;&nbsp;\<runtime></span></span>\
<span data-ttu-id="ccd43-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCNoAffinitize ></span><span class="sxs-lookup"><span data-stu-id="ccd43-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCNoAffinitize></span></span>

## <a name="syntax"></a><span data-ttu-id="ccd43-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ccd43-107">Syntax</span></span>

```xml
<GCNoAffinitize
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ccd43-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ccd43-108">Attributes and elements</span></span>

<span data-ttu-id="ccd43-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ccd43-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ccd43-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="ccd43-110">Attributes</span></span>

|<span data-ttu-id="ccd43-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="ccd43-111">Attribute</span></span>|<span data-ttu-id="ccd43-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ccd43-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="ccd43-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="ccd43-113">Required attribute.</span></span><br /><br /><span data-ttu-id="ccd43-114">Especifica se segmentos/heaps GC do servidor são relacionados com os processadores disponíveis no computador.</span><span class="sxs-lookup"><span data-stu-id="ccd43-114">Specifies whether server GC threads/heaps are affinitized with the processors available on the machine.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="ccd43-115">atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="ccd43-115">enabled attribute</span></span>

|<span data-ttu-id="ccd43-116">Valor</span><span class="sxs-lookup"><span data-stu-id="ccd43-116">Value</span></span>|<span data-ttu-id="ccd43-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="ccd43-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="ccd43-118">Threads GC do affinitizes Server com CPUs.</span><span class="sxs-lookup"><span data-stu-id="ccd43-118">Affinitizes server GC threads with CPUs.</span></span> <span data-ttu-id="ccd43-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="ccd43-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="ccd43-120">Não relacionar threads GC do servidor com CPUs.</span><span class="sxs-lookup"><span data-stu-id="ccd43-120">Does not affinitize server GC threads with CPUs.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ccd43-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ccd43-121">Child elements</span></span>

<span data-ttu-id="ccd43-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ccd43-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ccd43-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ccd43-123">Parent elements</span></span>

|<span data-ttu-id="ccd43-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="ccd43-124">Element</span></span>|<span data-ttu-id="ccd43-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="ccd43-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="ccd43-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ccd43-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="ccd43-127">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="ccd43-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ccd43-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="ccd43-128">Remarks</span></span>

<span data-ttu-id="ccd43-129">Por padrão, os threads GC do servidor são relacionados com suas respectivas CPUs.</span><span class="sxs-lookup"><span data-stu-id="ccd43-129">By default, server GC threads are hard-affinitized with their respective CPUs.</span></span> <span data-ttu-id="ccd43-130">Cada um dos processadores disponíveis do sistema tem seu próprio heap e thread de GC.</span><span class="sxs-lookup"><span data-stu-id="ccd43-130">Each of the system's available processors has its own GC heap and thread.</span></span> <span data-ttu-id="ccd43-131">Normalmente, essa é a configuração preferida, pois otimiza o uso do cache.</span><span class="sxs-lookup"><span data-stu-id="ccd43-131">This is typically the preferred setting since it optimizes cache usage.</span></span> <span data-ttu-id="ccd43-132">Começando com .NET Framework 4.6.2, definindo o atributo `enabled` do elemento **GCNoAffinitize** como `false`, você pode especificar que os threads GC do servidor e as CPUs não devem estar rigidamente acoplados.</span><span class="sxs-lookup"><span data-stu-id="ccd43-132">Starting with .NET Framework 4.6.2, by setting the **GCNoAffinitize** element's `enabled` attribute to `false`, you can specify that server GC threads and CPUs should not be tightly coupled.</span></span>

<span data-ttu-id="ccd43-133">Você pode especificar o elemento de configuração **GCNoAffinitize** sozinho para não relacionar THREADs GC de servidor com CPUs.</span><span class="sxs-lookup"><span data-stu-id="ccd43-133">You can specify the **GCNoAffinitize** configuration element alone to not affinitize server GC threads with CPUs.</span></span> <span data-ttu-id="ccd43-134">Você também pode usá-lo junto com o elemento [GCHeapCount](gcheapcount-element.md) para controlar o número de heaps e threads de GC usados por um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ccd43-134">You can also use it along with the [GCHeapCount](gcheapcount-element.md) element to control the number of GC heaps and threads used by an application.</span></span>

<span data-ttu-id="ccd43-135">Se o atributo `enabled` do elemento **GCNoAffinitize** for `false` (seu valor padrão), você também poderá usar o elemento [GCHeapCount](gcheapcount-element.md) para especificar o número de threads e heaps do GC, juntamente com o elemento [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md) para especificar os processadores aos quais os threads e heaps do GC são relacionados.</span><span class="sxs-lookup"><span data-stu-id="ccd43-135">If the `enabled` attribute of the **GCNoAffinitize** element is `false` (its default value), you can also use the [GCHeapCount](gcheapcount-element.md) element to specify the number of GC threads and heaps, along with the [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md) element to specify the processors to which the GC threads and heaps are affinitized.</span></span>

## <a name="example"></a><span data-ttu-id="ccd43-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ccd43-136">Example</span></span>

<span data-ttu-id="ccd43-137">O exemplo a seguir não relacionar os threads GC do servidor:</span><span class="sxs-lookup"><span data-stu-id="ccd43-137">The following example does not hard-affinitize server GC threads:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

<span data-ttu-id="ccd43-138">O exemplo a seguir não relacionar threads GC do servidor e limita o número de heaps/threads do GC a 10:</span><span class="sxs-lookup"><span data-stu-id="ccd43-138">The following example does not affinitize server GC threads and limits the number of GC heaps/threads to 10:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="ccd43-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ccd43-139">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="ccd43-140">Elemento GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="ccd43-140">GCHeapAffinitizeMask element</span></span>](gcheapaffinitizemask-element.md)
- [<span data-ttu-id="ccd43-141">Elemento GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="ccd43-141">GCHeapCount element</span></span>](gcheapcount-element.md)
- [<span data-ttu-id="ccd43-142">Noções básicas da coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="ccd43-142">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="ccd43-143">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="ccd43-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ccd43-144">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="ccd43-144">Configuration File Schema</span></span>](../index.md)
