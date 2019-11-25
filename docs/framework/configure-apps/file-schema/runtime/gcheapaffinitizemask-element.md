---
title: Elemento GCHeapAffinitizeMask
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 09d6523fb10692dd3617a3827d5bccf112bc632b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978378"
---
# <a name="gcheapaffinitizemask-element"></a><span data-ttu-id="0b644-102">\<elemento de > GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="0b644-102">\<GCHeapAffinitizeMask> element</span></span>

<span data-ttu-id="0b644-103">Define a afinidade entre heaps de GC e processadores individuais.</span><span class="sxs-lookup"><span data-stu-id="0b644-103">Defines the affinity between GC heaps and individual processors.</span></span>

<span data-ttu-id="0b644-104">> de configuração do \<</span><span class="sxs-lookup"><span data-stu-id="0b644-104">\<configuration></span></span>\
<span data-ttu-id="0b644-105">> &nbsp;de \<de tempo de execução do &nbsp;</span><span class="sxs-lookup"><span data-stu-id="0b644-105">&nbsp;&nbsp;\<runtime></span></span>\
<span data-ttu-id="0b644-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapAffinitizeMask ></span><span class="sxs-lookup"><span data-stu-id="0b644-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapAffinitizeMask></span></span>

## <a name="syntax"></a><span data-ttu-id="0b644-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0b644-107">Syntax</span></span>

```xml
<GCHeapAffinitizeMask
   enabled="nnnn"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0b644-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0b644-108">Attributes and elements</span></span>

<span data-ttu-id="0b644-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0b644-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0b644-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="0b644-110">Attributes</span></span>

|<span data-ttu-id="0b644-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="0b644-111">Attribute</span></span>|<span data-ttu-id="0b644-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b644-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="0b644-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="0b644-113">Required attribute.</span></span><br /><br /><span data-ttu-id="0b644-114">Especifica a afinidade entre heaps de GC e processadores individuais.</span><span class="sxs-lookup"><span data-stu-id="0b644-114">Specifies the affinity between GC heaps and individual processors.</span></span> |

#### <a name="enabled-attribute"></a><span data-ttu-id="0b644-115">atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="0b644-115">enabled attribute</span></span>

|<span data-ttu-id="0b644-116">Valor</span><span class="sxs-lookup"><span data-stu-id="0b644-116">Value</span></span>|<span data-ttu-id="0b644-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b644-117">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="0b644-118">Um valor decimal que forma um bitmask que define a afinidade entre heaps de GC de servidor e processadores individuais.</span><span class="sxs-lookup"><span data-stu-id="0b644-118">A decimal value that forms a bitmask defining the affinity between server GC heaps and individual processors.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="0b644-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0b644-119">Child elements</span></span>

<span data-ttu-id="0b644-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0b644-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0b644-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0b644-121">Parent elements</span></span>

|<span data-ttu-id="0b644-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="0b644-122">Element</span></span>|<span data-ttu-id="0b644-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b644-123">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="0b644-124">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0b644-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="0b644-125">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="0b644-125">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0b644-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="0b644-126">Remarks</span></span>

<span data-ttu-id="0b644-127">Por padrão, os threads GC do servidor são relacionados com sua respectiva CPU para que haja um heap de GC, um thread GC de servidor e um thread GC de servidor em segundo plano para cada processador.</span><span class="sxs-lookup"><span data-stu-id="0b644-127">By default, server GC threads are hard-affinitized with their respective CPU so that there is one GC heap, one server GC thread, and one background server GC thread for each processor.</span></span> <span data-ttu-id="0b644-128">A partir do .NET Framework 4.6.2, você pode usar o elemento **GCHeapAffinitizeMask** para controlar a afinidade entre heaps e processadores do GC do servidor quando o número de heaps é limitado pelo elemento **GCHeapCount** .</span><span class="sxs-lookup"><span data-stu-id="0b644-128">Starting with .NET Framework 4.6.2, you can use the **GCHeapAffinitizeMask** element to control the affinity between server GC heaps and processors when the number of heaps is limited by the **GCHeapCount** element.</span></span>

<span data-ttu-id="0b644-129">**GCHeapAffinitizeMask** normalmente é usado junto com dois outros sinalizadores:</span><span class="sxs-lookup"><span data-stu-id="0b644-129">**GCHeapAffinitizeMask** is typically used along with two other flags:</span></span>

- <span data-ttu-id="0b644-130">[GCNoAffinitize](gcnoaffinitize-element.md), que controla se threads GC do servidor/heaps são relacionados com CPUs.</span><span class="sxs-lookup"><span data-stu-id="0b644-130">[GCNoAffinitize](gcnoaffinitize-element.md), which controls whether server GC threads/heaps are affinitized with CPUs.</span></span> <span data-ttu-id="0b644-131">O atributo `enabled` do elemento [GCNoAffinitize](gcnoaffinitize-element.md) deve ser `false` (seu valor padrão) para que a configuração **GCHeapAffinitizeMask** seja usada.</span><span class="sxs-lookup"><span data-stu-id="0b644-131">The `enabled` attribute of the [GCNoAffinitize](gcnoaffinitize-element.md) element must be `false` (its default value) for the **GCHeapAffinitizeMask** setting to be used.</span></span>

- <span data-ttu-id="0b644-132">[GCHeapCount](gcheapcount-element.md), que limita o número de heaps usados pelo processo para GC do servidor.</span><span class="sxs-lookup"><span data-stu-id="0b644-132">[GCHeapCount](gcheapcount-element.md), which limits the number of heaps used by the process for server GC.</span></span> <span data-ttu-id="0b644-133">Por padrão, há um heap para cada processador.</span><span class="sxs-lookup"><span data-stu-id="0b644-133">By default, there is one heap for each processor.</span></span>

<span data-ttu-id="0b644-134">**nnnn** é uma máscara de bits expressa como um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="0b644-134">**nnnn** is a bit mask expressed as a decimal value.</span></span> <span data-ttu-id="0b644-135">O bit 0 do byte 0 representa o processador 0, o bit 1 do byte 0 representa o processador 1 e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="0b644-135">Bit 0 of byte 0 represents processor 0, bit 1 of byte 0 represents processor 1, and so on.</span></span> <span data-ttu-id="0b644-136">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="0b644-136">For example:</span></span>

```xml
<GCHeapAffinitizeMask enabled="1023"/>
```

<span data-ttu-id="0b644-137">Um valor de 1023 é 0x3FF ou 0011 1111 1111b.</span><span class="sxs-lookup"><span data-stu-id="0b644-137">A value of 1023 is 0x3FF or 0011 1111 1111b.</span></span> <span data-ttu-id="0b644-138">O processo usa 10 processadores, do processador 0 até o processador 9.</span><span class="sxs-lookup"><span data-stu-id="0b644-138">The process uses 10 processors, from processor 0 through processor 9.</span></span>

## <a name="example"></a><span data-ttu-id="0b644-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0b644-139">Example</span></span>

<span data-ttu-id="0b644-140">O exemplo a seguir indica que um aplicativo usa GC de servidor com 10 heaps/threads.</span><span class="sxs-lookup"><span data-stu-id="0b644-140">The following example indicates that an application uses server GC with 10 heaps/threads.</span></span> <span data-ttu-id="0b644-141">Como você não quer que esses heaps se sobreponham com heaps de outros aplicativos em execução no sistema, use **GCHeapAffinitizeMask** para especificar que o processo deve usar CPUs de 0 a 9.</span><span class="sxs-lookup"><span data-stu-id="0b644-141">Since you don't want those heaps to overlap with heaps from other applications running on the system, use **GCHeapAffinitizeMask** to specify that the process should use CPUs 0 through 9.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="0b644-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0b644-142">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="0b644-143">Elemento GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="0b644-143">GCNoAffinitize element</span></span>](gcnoaffinitize-element.md)
- [<span data-ttu-id="0b644-144">Elemento GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="0b644-144">GCHeapCount element</span></span>](gcheapcount-element.md)
- [<span data-ttu-id="0b644-145">Noções básicas da coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="0b644-145">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="0b644-146">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="0b644-146">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0b644-147">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="0b644-147">Configuration File Schema</span></span>](../index.md)
