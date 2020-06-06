---
title: Elemento GCHeapAffinitizeMask
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 09d6523fb10692dd3617a3827d5bccf112bc632b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73978378"
---
# <a name="gcheapaffinitizemask-element"></a><span data-ttu-id="1544e-102">Elemento \<GCHeapAffinitizeMask></span><span class="sxs-lookup"><span data-stu-id="1544e-102">\<GCHeapAffinitizeMask> element</span></span>

<span data-ttu-id="1544e-103">Define a afinidade entre heaps de GC e processadores individuais.</span><span class="sxs-lookup"><span data-stu-id="1544e-103">Defines the affinity between GC heaps and individual processors.</span></span>

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapAffinitizeMask>

## <a name="syntax"></a><span data-ttu-id="1544e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1544e-104">Syntax</span></span>

```xml
<GCHeapAffinitizeMask
   enabled="nnnn"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1544e-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1544e-105">Attributes and elements</span></span>

<span data-ttu-id="1544e-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1544e-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="1544e-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="1544e-107">Attributes</span></span>

|<span data-ttu-id="1544e-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="1544e-108">Attribute</span></span>|<span data-ttu-id="1544e-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="1544e-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="1544e-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="1544e-110">Required attribute.</span></span><br /><br /><span data-ttu-id="1544e-111">Especifica a afinidade entre heaps de GC e processadores individuais.</span><span class="sxs-lookup"><span data-stu-id="1544e-111">Specifies the affinity between GC heaps and individual processors.</span></span> |

#### <a name="enabled-attribute"></a><span data-ttu-id="1544e-112">atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="1544e-112">enabled attribute</span></span>

|<span data-ttu-id="1544e-113">Valor</span><span class="sxs-lookup"><span data-stu-id="1544e-113">Value</span></span>|<span data-ttu-id="1544e-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="1544e-114">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="1544e-115">Um valor decimal que forma um bitmask que define a afinidade entre heaps de GC de servidor e processadores individuais.</span><span class="sxs-lookup"><span data-stu-id="1544e-115">A decimal value that forms a bitmask defining the affinity between server GC heaps and individual processors.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="1544e-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1544e-116">Child elements</span></span>

<span data-ttu-id="1544e-117">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="1544e-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1544e-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1544e-118">Parent elements</span></span>

|<span data-ttu-id="1544e-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="1544e-119">Element</span></span>|<span data-ttu-id="1544e-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="1544e-120">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="1544e-121">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1544e-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="1544e-122">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="1544e-122">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1544e-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="1544e-123">Remarks</span></span>

<span data-ttu-id="1544e-124">Por padrão, os threads GC do servidor são relacionados com sua respectiva CPU para que haja um heap de GC, um thread GC de servidor e um thread GC de servidor em segundo plano para cada processador.</span><span class="sxs-lookup"><span data-stu-id="1544e-124">By default, server GC threads are hard-affinitized with their respective CPU so that there is one GC heap, one server GC thread, and one background server GC thread for each processor.</span></span> <span data-ttu-id="1544e-125">A partir do .NET Framework 4.6.2, você pode usar o elemento **GCHeapAffinitizeMask** para controlar a afinidade entre heaps e processadores do GC do servidor quando o número de heaps é limitado pelo elemento **GCHeapCount** .</span><span class="sxs-lookup"><span data-stu-id="1544e-125">Starting with .NET Framework 4.6.2, you can use the **GCHeapAffinitizeMask** element to control the affinity between server GC heaps and processors when the number of heaps is limited by the **GCHeapCount** element.</span></span>

<span data-ttu-id="1544e-126">**GCHeapAffinitizeMask** normalmente é usado junto com dois outros sinalizadores:</span><span class="sxs-lookup"><span data-stu-id="1544e-126">**GCHeapAffinitizeMask** is typically used along with two other flags:</span></span>

- <span data-ttu-id="1544e-127">[GCNoAffinitize](gcnoaffinitize-element.md), que controla se threads GC do servidor/heaps são relacionados com CPUs.</span><span class="sxs-lookup"><span data-stu-id="1544e-127">[GCNoAffinitize](gcnoaffinitize-element.md), which controls whether server GC threads/heaps are affinitized with CPUs.</span></span> <span data-ttu-id="1544e-128">O `enabled` atributo do elemento [GCNoAffinitize](gcnoaffinitize-element.md) deve ser `false` (seu valor padrão) para que a configuração **GCHeapAffinitizeMask** seja usada.</span><span class="sxs-lookup"><span data-stu-id="1544e-128">The `enabled` attribute of the [GCNoAffinitize](gcnoaffinitize-element.md) element must be `false` (its default value) for the **GCHeapAffinitizeMask** setting to be used.</span></span>

- <span data-ttu-id="1544e-129">[GCHeapCount](gcheapcount-element.md), que limita o número de heaps usados pelo processo para GC do servidor.</span><span class="sxs-lookup"><span data-stu-id="1544e-129">[GCHeapCount](gcheapcount-element.md), which limits the number of heaps used by the process for server GC.</span></span> <span data-ttu-id="1544e-130">Por padrão, há um heap para cada processador.</span><span class="sxs-lookup"><span data-stu-id="1544e-130">By default, there is one heap for each processor.</span></span>

<span data-ttu-id="1544e-131">**nnnn** é uma máscara de bits expressa como um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="1544e-131">**nnnn** is a bit mask expressed as a decimal value.</span></span> <span data-ttu-id="1544e-132">O bit 0 do byte 0 representa o processador 0, o bit 1 do byte 0 representa o processador 1 e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="1544e-132">Bit 0 of byte 0 represents processor 0, bit 1 of byte 0 represents processor 1, and so on.</span></span> <span data-ttu-id="1544e-133">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="1544e-133">For example:</span></span>

```xml
<GCHeapAffinitizeMask enabled="1023"/>
```

<span data-ttu-id="1544e-134">Um valor de 1023 é 0x3FF ou 0011 1111 1111b.</span><span class="sxs-lookup"><span data-stu-id="1544e-134">A value of 1023 is 0x3FF or 0011 1111 1111b.</span></span> <span data-ttu-id="1544e-135">O processo usa 10 processadores, do processador 0 até o processador 9.</span><span class="sxs-lookup"><span data-stu-id="1544e-135">The process uses 10 processors, from processor 0 through processor 9.</span></span>

## <a name="example"></a><span data-ttu-id="1544e-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1544e-136">Example</span></span>

<span data-ttu-id="1544e-137">O exemplo a seguir indica que um aplicativo usa GC de servidor com 10 heaps/threads.</span><span class="sxs-lookup"><span data-stu-id="1544e-137">The following example indicates that an application uses server GC with 10 heaps/threads.</span></span> <span data-ttu-id="1544e-138">Como você não quer que esses heaps se sobreponham com heaps de outros aplicativos em execução no sistema, use **GCHeapAffinitizeMask** para especificar que o processo deve usar CPUs de 0 a 9.</span><span class="sxs-lookup"><span data-stu-id="1544e-138">Since you don't want those heaps to overlap with heaps from other applications running on the system, use **GCHeapAffinitizeMask** to specify that the process should use CPUs 0 through 9.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="1544e-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="1544e-139">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="1544e-140">Elemento GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="1544e-140">GCNoAffinitize element</span></span>](gcnoaffinitize-element.md)
- [<span data-ttu-id="1544e-141">Elemento GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="1544e-141">GCHeapCount element</span></span>](gcheapcount-element.md)
- [<span data-ttu-id="1544e-142">Conceitos básicos da coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="1544e-142">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="1544e-143">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="1544e-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="1544e-144">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="1544e-144">Configuration File Schema</span></span>](../index.md)
