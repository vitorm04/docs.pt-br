---
title: Elemento GCNoAffinitize
ms.date: 11/08/2019
helpviewer_keywords:
- gcNoAffinitize element
- <gcNoAffinitize> element
ms.openlocfilehash: 16d6e5adefe2b632d7251669650058d7df7cea70
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "84004732"
---
# <a name="gcnoaffinitize-element"></a><span data-ttu-id="a07b2-102">Elemento \<GCNoAffinitize></span><span class="sxs-lookup"><span data-stu-id="a07b2-102">\<GCNoAffinitize> element</span></span>

<span data-ttu-id="a07b2-103">Especifica se os threads GC do servidor relacionar ou não devem ser usados com CPUs.</span><span class="sxs-lookup"><span data-stu-id="a07b2-103">Specifies whether or not to affinitize server GC threads with CPUs.</span></span>

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCNoAffinitize>

## <a name="syntax"></a><span data-ttu-id="a07b2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a07b2-104">Syntax</span></span>

```xml
<GCNoAffinitize
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a07b2-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a07b2-105">Attributes and elements</span></span>

<span data-ttu-id="a07b2-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a07b2-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a07b2-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="a07b2-107">Attributes</span></span>

|<span data-ttu-id="a07b2-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="a07b2-108">Attribute</span></span>|<span data-ttu-id="a07b2-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="a07b2-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="a07b2-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="a07b2-110">Required attribute.</span></span><br /><br /><span data-ttu-id="a07b2-111">Especifica se segmentos/heaps GC do servidor são relacionados com os processadores disponíveis no computador.</span><span class="sxs-lookup"><span data-stu-id="a07b2-111">Specifies whether server GC threads/heaps are affinitized with the processors available on the machine.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="a07b2-112">atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="a07b2-112">enabled attribute</span></span>

|<span data-ttu-id="a07b2-113">Valor</span><span class="sxs-lookup"><span data-stu-id="a07b2-113">Value</span></span>|<span data-ttu-id="a07b2-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="a07b2-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="a07b2-115">Threads GC do affinitizes Server com CPUs.</span><span class="sxs-lookup"><span data-stu-id="a07b2-115">Affinitizes server GC threads with CPUs.</span></span> <span data-ttu-id="a07b2-116">Este é o padrão.</span><span class="sxs-lookup"><span data-stu-id="a07b2-116">This is the default.</span></span>|
|`true`|<span data-ttu-id="a07b2-117">Não relacionar threads GC do servidor com CPUs.</span><span class="sxs-lookup"><span data-stu-id="a07b2-117">Does not affinitize server GC threads with CPUs.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="a07b2-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a07b2-118">Child elements</span></span>

<span data-ttu-id="a07b2-119">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a07b2-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a07b2-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a07b2-120">Parent elements</span></span>

|<span data-ttu-id="a07b2-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="a07b2-121">Element</span></span>|<span data-ttu-id="a07b2-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="a07b2-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="a07b2-123">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a07b2-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="a07b2-124">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="a07b2-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a07b2-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="a07b2-125">Remarks</span></span>

<span data-ttu-id="a07b2-126">Por padrão, os threads GC do servidor são relacionados com suas respectivas CPUs.</span><span class="sxs-lookup"><span data-stu-id="a07b2-126">By default, server GC threads are hard-affinitized with their respective CPUs.</span></span> <span data-ttu-id="a07b2-127">Cada um dos processadores disponíveis do sistema tem seu próprio heap e thread de GC.</span><span class="sxs-lookup"><span data-stu-id="a07b2-127">Each of the system's available processors has its own GC heap and thread.</span></span> <span data-ttu-id="a07b2-128">Normalmente, essa é a configuração preferida, pois otimiza o uso do cache.</span><span class="sxs-lookup"><span data-stu-id="a07b2-128">This is typically the preferred setting since it optimizes cache usage.</span></span> <span data-ttu-id="a07b2-129">Começando com .NET Framework 4.6.2, definindo o atributo **GCNoAffinitize** do elemento GCNoAffinitize `enabled` como `true` , você pode especificar que os threads e as CPUs do servidor GC não devem estar rigidamente acoplados.</span><span class="sxs-lookup"><span data-stu-id="a07b2-129">Starting with .NET Framework 4.6.2, by setting the **GCNoAffinitize** element's `enabled` attribute to `true`, you can specify that server GC threads and CPUs should not be tightly coupled.</span></span>

<span data-ttu-id="a07b2-130">Você pode especificar o elemento de configuração **GCNoAffinitize** sozinho para não relacionar THREADs GC de servidor com CPUs.</span><span class="sxs-lookup"><span data-stu-id="a07b2-130">You can specify the **GCNoAffinitize** configuration element alone to not affinitize server GC threads with CPUs.</span></span> <span data-ttu-id="a07b2-131">Você também pode usá-lo junto com o elemento [GCHeapCount](gcheapcount-element.md) para controlar o número de heaps e threads de GC usados por um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a07b2-131">You can also use it along with the [GCHeapCount](gcheapcount-element.md) element to control the number of GC heaps and threads used by an application.</span></span>

<span data-ttu-id="a07b2-132">Se o `enabled` atributo do elemento **GCNoAffinitize** for `false` (seu valor padrão), você também poderá usar o elemento [GCHeapCount](gcheapcount-element.md) para especificar o número de threads e heaps do GC, juntamente com o elemento [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md) para especificar os processadores aos quais os threads e heaps do GC são relacionados.</span><span class="sxs-lookup"><span data-stu-id="a07b2-132">If the `enabled` attribute of the **GCNoAffinitize** element is `false` (its default value), you can also use the [GCHeapCount](gcheapcount-element.md) element to specify the number of GC threads and heaps, along with the [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md) element to specify the processors to which the GC threads and heaps are affinitized.</span></span>

## <a name="example"></a><span data-ttu-id="a07b2-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a07b2-133">Example</span></span>

<span data-ttu-id="a07b2-134">O exemplo a seguir não relacionar os threads GC do servidor:</span><span class="sxs-lookup"><span data-stu-id="a07b2-134">The following example does not hard-affinitize server GC threads:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

<span data-ttu-id="a07b2-135">O exemplo a seguir não relacionar threads GC do servidor e limita o número de heaps/threads do GC a 10:</span><span class="sxs-lookup"><span data-stu-id="a07b2-135">The following example does not affinitize server GC threads and limits the number of GC heaps/threads to 10:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="a07b2-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="a07b2-136">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a07b2-137">Elemento GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="a07b2-137">GCHeapAffinitizeMask element</span></span>](gcheapaffinitizemask-element.md)
- [<span data-ttu-id="a07b2-138">Elemento GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="a07b2-138">GCHeapCount element</span></span>](gcheapcount-element.md)
- [<span data-ttu-id="a07b2-139">Conceitos básicos da coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="a07b2-139">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="a07b2-140">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="a07b2-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a07b2-141">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="a07b2-141">Configuration File Schema</span></span>](../index.md)
