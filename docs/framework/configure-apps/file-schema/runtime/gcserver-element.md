---
title: Elemento gcServer
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
ms.openlocfilehash: 8eab5e36bab90510aff4f1a3e15328197ac59ed7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73968941"
---
# <a name="gcserver-element"></a><span data-ttu-id="9c0c1-102">Elemento \<gcServer></span><span class="sxs-lookup"><span data-stu-id="9c0c1-102">\<gcServer> element</span></span>

<span data-ttu-id="9c0c1-103">Especifica se o Common Language Runtime executa a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="9c0c1-103">Specifies whether the common language runtime runs server garbage collection.</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcServer>

## <a name="syntax"></a><span data-ttu-id="9c0c1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9c0c1-104">Syntax</span></span>

```xml
<gcServer
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9c0c1-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9c0c1-105">Attributes and elements</span></span>

<span data-ttu-id="9c0c1-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9c0c1-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9c0c1-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="9c0c1-107">Attributes</span></span>

|<span data-ttu-id="9c0c1-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="9c0c1-108">Attribute</span></span>|<span data-ttu-id="9c0c1-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c0c1-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="9c0c1-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="9c0c1-110">Required attribute.</span></span><br /><br /><span data-ttu-id="9c0c1-111">Especifica se o tempo de execução executa a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="9c0c1-111">Specifies whether the runtime runs server garbage collection.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="9c0c1-112">atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="9c0c1-112">enabled attribute</span></span>

|<span data-ttu-id="9c0c1-113">Valor</span><span class="sxs-lookup"><span data-stu-id="9c0c1-113">Value</span></span>|<span data-ttu-id="9c0c1-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c0c1-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="9c0c1-115">Não executa a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="9c0c1-115">Does not run server garbage collection.</span></span> <span data-ttu-id="9c0c1-116">Este é o padrão.</span><span class="sxs-lookup"><span data-stu-id="9c0c1-116">This is the default.</span></span>|
|`true`|<span data-ttu-id="9c0c1-117">Executa a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="9c0c1-117">Runs server garbage collection.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="9c0c1-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9c0c1-118">Child elements</span></span>

<span data-ttu-id="9c0c1-119">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="9c0c1-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9c0c1-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9c0c1-120">Parent elements</span></span>

|<span data-ttu-id="9c0c1-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="9c0c1-121">Element</span></span>|<span data-ttu-id="9c0c1-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c0c1-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="9c0c1-123">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9c0c1-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="9c0c1-124">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="9c0c1-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9c0c1-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="9c0c1-125">Remarks</span></span>

<span data-ttu-id="9c0c1-126">O Common Language Runtime (CLR) dá suporte a dois tipos de coleta de lixo: coleta de lixo da estação de trabalho, que está disponível em todos os sistemas e coleta de lixo do servidor, que está disponível em sistemas de multiprocessadores.</span><span class="sxs-lookup"><span data-stu-id="9c0c1-126">The common language runtime (CLR) supports two types of garbage collection: workstation garbage collection, which is available on all systems, and server garbage collection, which is available on multiprocessor systems.</span></span> <span data-ttu-id="9c0c1-127">Use o elemento **gcServer** para controlar o tipo de coleta de lixo que o CLR executa.</span><span class="sxs-lookup"><span data-stu-id="9c0c1-127">Use the **gcServer** element to control the type of garbage collection the CLR performs.</span></span> <span data-ttu-id="9c0c1-128">Use a <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> propriedade para determinar se a coleta de lixo do servidor está habilitada.</span><span class="sxs-lookup"><span data-stu-id="9c0c1-128">Use the <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> property to determine if server garbage collection is enabled.</span></span>

<span data-ttu-id="9c0c1-129">Para computadores com um único processador, a coleta de lixo da estação de trabalho padrão deve ser a opção mais rápida.</span><span class="sxs-lookup"><span data-stu-id="9c0c1-129">For single-processor computers, the default workstation garbage collection should be the fastest option.</span></span> <span data-ttu-id="9c0c1-130">A estação de trabalho ou o servidor pode ser usado para computadores com dois processadores.</span><span class="sxs-lookup"><span data-stu-id="9c0c1-130">Either workstation or server can be used for two-processor computers.</span></span> <span data-ttu-id="9c0c1-131">A coleta de lixo do servidor deve ser a opção mais rápida para mais de dois processadores.</span><span class="sxs-lookup"><span data-stu-id="9c0c1-131">Server garbage collection should be the fastest option for more than two processors.</span></span> <span data-ttu-id="9c0c1-132">Normalmente, os sistemas de servidores multiprocessadores desabilitam o GC do servidor e usam o GC da estação de trabalho quando muitas instâncias de um aplicativo de servidor são executadas no mesmo computador.</span><span class="sxs-lookup"><span data-stu-id="9c0c1-132">Most commonly, multiprocessor server systems disable server GC and use workstation GC instead when many instances of a server app run on the same machine.</span></span>

<span data-ttu-id="9c0c1-133">Esse elemento só pode ser usado no arquivo de configuração do aplicativo; Ela será ignorada se estiver no arquivo de configuração da máquina.</span><span class="sxs-lookup"><span data-stu-id="9c0c1-133">This element can be used only in the application configuration file; it is ignored if it is in the machine configuration file.</span></span>

> [!NOTE]
> <span data-ttu-id="9c0c1-134">No .NET Framework 4 e versões anteriores, a coleta de lixo simultânea não está disponível quando a coleta de lixo do servidor está habilitada.</span><span class="sxs-lookup"><span data-stu-id="9c0c1-134">In the .NET Framework 4 and earlier versions, concurrent garbage collection is not available when server garbage collection is enabled.</span></span> <span data-ttu-id="9c0c1-135">A partir do .NET Framework 4,5, a coleta de lixo do servidor é simultânea.</span><span class="sxs-lookup"><span data-stu-id="9c0c1-135">Starting with the .NET Framework 4.5, server garbage collection is concurrent.</span></span> <span data-ttu-id="9c0c1-136">Para usar a coleta de lixo do servidor não simultânea, defina o elemento **gcServer** como `true` e o [elemento gcConcurrent](gcconcurrent-element.md) como `false` .</span><span class="sxs-lookup"><span data-stu-id="9c0c1-136">To use non-concurrent server garbage collection, set the **gcServer** element to `true` and the [gcConcurrent element](gcconcurrent-element.md) to `false`.</span></span>

<span data-ttu-id="9c0c1-137">A partir do .NET Framework 4.6.2, você também pode usar os seguintes elementos para configurar o GC do servidor:</span><span class="sxs-lookup"><span data-stu-id="9c0c1-137">Starting with .NET Framework 4.6.2, you can also use the following elements to configure server GC:</span></span>

- <span data-ttu-id="9c0c1-138">[GCNoAffinitize](gcnoaffinitize-element.md), que especifica se há uma afinidade entre os processadores e heaps do GC do servidor.</span><span class="sxs-lookup"><span data-stu-id="9c0c1-138">[GCNoAffinitize](gcnoaffinitize-element.md), which specifies whether there is an affinity between server GC heaps and processors.</span></span> <span data-ttu-id="9c0c1-139">Por padrão, há um heap GC de servidor para cada processador.</span><span class="sxs-lookup"><span data-stu-id="9c0c1-139">By default, there is one server GC heap for each processor.</span></span>

- <span data-ttu-id="9c0c1-140">[GCHeapCount](gcheapcount-element.md), que limita o número de heaps usados por um processo.</span><span class="sxs-lookup"><span data-stu-id="9c0c1-140">[GCHeapCount](gcheapcount-element.md), which limits the number of heaps used by a process.</span></span>

- <span data-ttu-id="9c0c1-141">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), que define a afinidade entre as pilhas de GC do servidor disponíveis e os processadores individuais.</span><span class="sxs-lookup"><span data-stu-id="9c0c1-141">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), which defines the affinity between the available server GC heaps and individual processors.</span></span>

## <a name="example"></a><span data-ttu-id="9c0c1-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9c0c1-142">Example</span></span>

<span data-ttu-id="9c0c1-143">O exemplo a seguir habilita a coleta de lixo do servidor:</span><span class="sxs-lookup"><span data-stu-id="9c0c1-143">The following example enables server garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="9c0c1-144">Confira também</span><span class="sxs-lookup"><span data-stu-id="9c0c1-144">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="9c0c1-145">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="9c0c1-145">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9c0c1-146">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="9c0c1-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="9c0c1-147">Para desabilitar a coleta de lixo simultânea</span><span class="sxs-lookup"><span data-stu-id="9c0c1-147">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
