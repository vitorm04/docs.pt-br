---
title: Elemento GCHeapCount
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 3d6cac4185af182758cb82e6bfd9d96ed24869b4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283079"
---
# <a name="gcheapcount-element"></a><span data-ttu-id="1b7c0-102">\<elemento de > GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="1b7c0-102">\<GCHeapCount> element</span></span>

<span data-ttu-id="1b7c0-103">Especifica o número de heaps/threads a serem usados para a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="1b7c0-103">Specifies the number of heaps/threads to use for server garbage collection.</span></span>

<span data-ttu-id="1b7c0-104">> de configuração do \<</span><span class="sxs-lookup"><span data-stu-id="1b7c0-104">\<configuration></span></span>\
<span data-ttu-id="1b7c0-105">> &nbsp;de \<de tempo de execução do &nbsp;</span><span class="sxs-lookup"><span data-stu-id="1b7c0-105">&nbsp;&nbsp;\<runtime></span></span>\
<span data-ttu-id="1b7c0-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapCount ></span><span class="sxs-lookup"><span data-stu-id="1b7c0-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapCount></span></span>

## <a name="syntax"></a><span data-ttu-id="1b7c0-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1b7c0-107">Syntax</span></span>

```xml
<GCHeapCount
   enabled="nn"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1b7c0-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1b7c0-108">Attributes and elements</span></span>

<span data-ttu-id="1b7c0-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1b7c0-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="1b7c0-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="1b7c0-110">Attributes</span></span>

|<span data-ttu-id="1b7c0-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="1b7c0-111">Attribute</span></span>|<span data-ttu-id="1b7c0-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="1b7c0-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="1b7c0-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="1b7c0-113">Required attribute.</span></span><br /><br /><span data-ttu-id="1b7c0-114">Especifica o número de heaps a ser usado para a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="1b7c0-114">Specifies the number of heaps to use for server garbage collection.</span></span> <span data-ttu-id="1b7c0-115">O número real de heaps é o mínimo do número de heaps que você especifica e o número de processadores que seu processo tem permissão para usar.</span><span class="sxs-lookup"><span data-stu-id="1b7c0-115">The actual number of heaps is the minimum of the number of heaps you specify and the number of processors your process is allowed to use.</span></span> |

#### <a name="enabled-attribute"></a><span data-ttu-id="1b7c0-116">atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="1b7c0-116">enabled attribute</span></span>

|<span data-ttu-id="1b7c0-117">Valor</span><span class="sxs-lookup"><span data-stu-id="1b7c0-117">Value</span></span>|<span data-ttu-id="1b7c0-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="1b7c0-118">Description</span></span>|
|-----------|-----------------|
|`nn`|<span data-ttu-id="1b7c0-119">O número de heaps a ser usado para o GC do servidor.</span><span class="sxs-lookup"><span data-stu-id="1b7c0-119">The number of heaps to use for server GC.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="1b7c0-120">Child elements</span><span class="sxs-lookup"><span data-stu-id="1b7c0-120">Child elements</span></span>

<span data-ttu-id="1b7c0-121">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="1b7c0-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1b7c0-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1b7c0-122">Parent elements</span></span>

|<span data-ttu-id="1b7c0-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="1b7c0-123">Element</span></span>|<span data-ttu-id="1b7c0-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="1b7c0-124">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="1b7c0-125">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1b7c0-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="1b7c0-126">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="1b7c0-126">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1b7c0-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="1b7c0-127">Remarks</span></span>

<span data-ttu-id="1b7c0-128">Por padrão, os threads GC do servidor são relacionados com sua respectiva CPU para que haja um heap de GC, um thread GC de servidor e um thread GC de servidor em segundo plano para cada processador.</span><span class="sxs-lookup"><span data-stu-id="1b7c0-128">By default, server GC threads are hard-affinitized with their respective CPU so that there is one GC heap, one server GC thread, and one background server GC thread for each processor.</span></span> <span data-ttu-id="1b7c0-129">Começando com .NET Framework 4.6.2, você pode usar o elemento **GCHeapCount** para limitar o número de heaps usados pelo seu aplicativo para GC de servidor.</span><span class="sxs-lookup"><span data-stu-id="1b7c0-129">Starting with .NET Framework 4.6.2, you can use the **GCHeapCount** element to limit the number of heaps used by your application for server GC.</span></span> <span data-ttu-id="1b7c0-130">Limitar o número de heaps usado para o servidor GC é particularmente útil para sistemas que executam várias instâncias de um aplicativo de servidor.</span><span class="sxs-lookup"><span data-stu-id="1b7c0-130">Limiting the number of heaps used for server GC is particularly useful for systems that run multiple instances of a server application.</span></span>

<span data-ttu-id="1b7c0-131">**GCHeapCount** normalmente é usado junto com dois outros sinalizadores:</span><span class="sxs-lookup"><span data-stu-id="1b7c0-131">**GCHeapCount** is typically used along with two other flags:</span></span>

- <span data-ttu-id="1b7c0-132">[GCNoAffinitize](gcnoaffinitize-element.md), que controla se threads GC do servidor/heaps são relacionados com CPUs.</span><span class="sxs-lookup"><span data-stu-id="1b7c0-132">[GCNoAffinitize](gcnoaffinitize-element.md), which controls whether server GC threads/heaps are affinitized with CPUs.</span></span>

- <span data-ttu-id="1b7c0-133">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), que controla a afinidade de threads do GC/heaps com CPUs.</span><span class="sxs-lookup"><span data-stu-id="1b7c0-133">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), which controls the affinity of GC threads/heaps with CPUs.</span></span>

<span data-ttu-id="1b7c0-134">Se **GCHeapCount** for definido e **GCNoAffinitize** estiver desabilitado (sua configuração padrão), haverá uma afinidade entre os threads/pilhas do *NN* GC e os primeiros processadores *NN* .</span><span class="sxs-lookup"><span data-stu-id="1b7c0-134">If **GCHeapCount** is set and **GCNoAffinitize** is disabled (its default setting), there is an affinity between the *nn* GC threads/heaps and the first *nn* processors.</span></span> <span data-ttu-id="1b7c0-135">Você pode usar o elemento **GCHeapAffinitizeMask** para especificar quais processadores são usados pelos heaps de GC do servidor do processo.</span><span class="sxs-lookup"><span data-stu-id="1b7c0-135">You can use the **GCHeapAffinitizeMask** element to specify which processors are used by the process's server GC heaps.</span></span> <span data-ttu-id="1b7c0-136">Caso contrário, se vários processos de servidor estiverem em execução em um sistema, o uso do processador será sobreposto.</span><span class="sxs-lookup"><span data-stu-id="1b7c0-136">Otherwise, if multiple server processes are running on a system, their processor usage will overlap.</span></span>

<span data-ttu-id="1b7c0-137">Se **GCHeapCount** for definido e **GCNoAffinitize** estiver habilitado, o coletor de lixo limita o número de processadores usados para GC do servidor, mas não relacionar heaps e processadores do GC.</span><span class="sxs-lookup"><span data-stu-id="1b7c0-137">If **GCHeapCount** is set and **GCNoAffinitize** is enabled, the garbage collector limits the number of processors used for server GC but does not affinitize GC heaps and processors.</span></span>

## <a name="example"></a><span data-ttu-id="1b7c0-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1b7c0-138">Example</span></span>

<span data-ttu-id="1b7c0-139">O exemplo a seguir indica que um aplicativo usa GC de servidor com 10 heaps/threads.</span><span class="sxs-lookup"><span data-stu-id="1b7c0-139">The following example indicates that an application uses server GC with 10 heaps/threads.</span></span> <span data-ttu-id="1b7c0-140">Como você não quer que esses heaps se sobreponham com heaps de outros aplicativos em execução no sistema, use o **GCHeapAffinitizeMask** para especificar que o processo deve usar CPUs de 0 a 9.</span><span class="sxs-lookup"><span data-stu-id="1b7c0-140">Since you don't want those heaps to overlap with heaps from other applications running on the system, you use the **GCHeapAffinitizeMask** to specify that the process should use CPUs 0 through 9.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

<span data-ttu-id="1b7c0-141">O exemplo a seguir não relacionar threads GC do servidor e limita o número de heaps/threads do GC a 10.</span><span class="sxs-lookup"><span data-stu-id="1b7c0-141">The following example does not affinitize server GC threads and limits the number of GC heaps/threads to 10.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="1b7c0-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1b7c0-142">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="1b7c0-143">Elemento GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="1b7c0-143">GCNoAffinitize element</span></span>](gcnoaffinitize-element.md)
- [<span data-ttu-id="1b7c0-144">Elemento GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="1b7c0-144">GCHeapAffinitizeMask element</span></span>](gcheapaffinitizemask-element.md)
- [<span data-ttu-id="1b7c0-145">Noções básicas da coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="1b7c0-145">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="1b7c0-146">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="1b7c0-146">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="1b7c0-147">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="1b7c0-147">Configuration File Schema</span></span>](../index.md)
