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
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968941"
---
# <a name="gcserver-element"></a><span data-ttu-id="a6777-102">\<elemento de > gcServer</span><span class="sxs-lookup"><span data-stu-id="a6777-102">\<gcServer> element</span></span>

<span data-ttu-id="a6777-103">Especifica se o Common Language Runtime executa a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="a6777-103">Specifies whether the common language runtime runs server garbage collection.</span></span>

<span data-ttu-id="a6777-104">[\<configuration>](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a6777-104">[\<configuration>](../configuration-element.md)</span></span>\
<span data-ttu-id="a6777-105">> &nbsp;de [\<de tempo de execução](runtime-element.md) do &nbsp;</span><span class="sxs-lookup"><span data-stu-id="a6777-105">&nbsp;&nbsp;[\<runtime>](runtime-element.md)</span></span>\
<span data-ttu-id="a6777-106">&nbsp;&nbsp;&nbsp;&nbsp;\<gcServer ></span><span class="sxs-lookup"><span data-stu-id="a6777-106">&nbsp;&nbsp;&nbsp;&nbsp;\<gcServer></span></span>

## <a name="syntax"></a><span data-ttu-id="a6777-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a6777-107">Syntax</span></span>

```xml
<gcServer
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a6777-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a6777-108">Attributes and elements</span></span>

<span data-ttu-id="a6777-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a6777-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a6777-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="a6777-110">Attributes</span></span>

|<span data-ttu-id="a6777-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="a6777-111">Attribute</span></span>|<span data-ttu-id="a6777-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6777-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="a6777-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="a6777-113">Required attribute.</span></span><br /><br /><span data-ttu-id="a6777-114">Especifica se o tempo de execução executa a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="a6777-114">Specifies whether the runtime runs server garbage collection.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="a6777-115">atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="a6777-115">enabled attribute</span></span>

|<span data-ttu-id="a6777-116">Valor</span><span class="sxs-lookup"><span data-stu-id="a6777-116">Value</span></span>|<span data-ttu-id="a6777-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6777-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="a6777-118">Não executa a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="a6777-118">Does not run server garbage collection.</span></span> <span data-ttu-id="a6777-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="a6777-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="a6777-120">Executa a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="a6777-120">Runs server garbage collection.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="a6777-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a6777-121">Child elements</span></span>

<span data-ttu-id="a6777-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a6777-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a6777-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a6777-123">Parent elements</span></span>

|<span data-ttu-id="a6777-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="a6777-124">Element</span></span>|<span data-ttu-id="a6777-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6777-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="a6777-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a6777-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="a6777-127">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="a6777-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a6777-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="a6777-128">Remarks</span></span>

<span data-ttu-id="a6777-129">O Common Language Runtime (CLR) dá suporte a dois tipos de coleta de lixo: coleta de lixo da estação de trabalho, que está disponível em todos os sistemas e coleta de lixo do servidor, que está disponível em sistemas de multiprocessadores.</span><span class="sxs-lookup"><span data-stu-id="a6777-129">The common language runtime (CLR) supports two types of garbage collection: workstation garbage collection, which is available on all systems, and server garbage collection, which is available on multiprocessor systems.</span></span> <span data-ttu-id="a6777-130">Use o elemento **gcServer** para controlar o tipo de coleta de lixo que o CLR executa.</span><span class="sxs-lookup"><span data-stu-id="a6777-130">Use the **gcServer** element to control the type of garbage collection the CLR performs.</span></span> <span data-ttu-id="a6777-131">Use a propriedade <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> para determinar se a coleta de lixo do servidor está habilitada.</span><span class="sxs-lookup"><span data-stu-id="a6777-131">Use the <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> property to determine if server garbage collection is enabled.</span></span>

<span data-ttu-id="a6777-132">Para computadores com um único processador, a coleta de lixo da estação de trabalho padrão deve ser a opção mais rápida.</span><span class="sxs-lookup"><span data-stu-id="a6777-132">For single-processor computers, the default workstation garbage collection should be the fastest option.</span></span> <span data-ttu-id="a6777-133">A estação de trabalho ou o servidor pode ser usado para computadores com dois processadores.</span><span class="sxs-lookup"><span data-stu-id="a6777-133">Either workstation or server can be used for two-processor computers.</span></span> <span data-ttu-id="a6777-134">A coleta de lixo do servidor deve ser a opção mais rápida para mais de dois processadores.</span><span class="sxs-lookup"><span data-stu-id="a6777-134">Server garbage collection should be the fastest option for more than two processors.</span></span> <span data-ttu-id="a6777-135">Normalmente, os sistemas de servidores multiprocessadores desabilitam o GC do servidor e usam o GC da estação de trabalho quando muitas instâncias de um aplicativo de servidor são executadas no mesmo computador.</span><span class="sxs-lookup"><span data-stu-id="a6777-135">Most commonly, multiprocessor server systems disable server GC and use workstation GC instead when many instances of a server app run on the same machine.</span></span>

<span data-ttu-id="a6777-136">Esse elemento só pode ser usado no arquivo de configuração do aplicativo; Ela será ignorada se estiver no arquivo de configuração da máquina.</span><span class="sxs-lookup"><span data-stu-id="a6777-136">This element can be used only in the application configuration file; it is ignored if it is in the machine configuration file.</span></span>

> [!NOTE]
> <span data-ttu-id="a6777-137">No .NET Framework 4 e versões anteriores, a coleta de lixo simultânea não está disponível quando a coleta de lixo do servidor está habilitada.</span><span class="sxs-lookup"><span data-stu-id="a6777-137">In the .NET Framework 4 and earlier versions, concurrent garbage collection is not available when server garbage collection is enabled.</span></span> <span data-ttu-id="a6777-138">A partir do .NET Framework 4,5, a coleta de lixo do servidor é simultânea.</span><span class="sxs-lookup"><span data-stu-id="a6777-138">Starting with the .NET Framework 4.5, server garbage collection is concurrent.</span></span> <span data-ttu-id="a6777-139">Para usar a coleta de lixo do servidor não simultânea, defina o elemento **gcServer** como `true` e o [elemento gcConcurrent](gcconcurrent-element.md) como `false`.</span><span class="sxs-lookup"><span data-stu-id="a6777-139">To use non-concurrent server garbage collection, set the **gcServer** element to `true` and the [gcConcurrent element](gcconcurrent-element.md) to `false`.</span></span>

<span data-ttu-id="a6777-140">A partir do .NET Framework 4.6.2, você também pode usar os seguintes elementos para configurar o GC do servidor:</span><span class="sxs-lookup"><span data-stu-id="a6777-140">Starting with .NET Framework 4.6.2, you can also use the following elements to configure server GC:</span></span>

- <span data-ttu-id="a6777-141">[GCNoAffinitize](gcnoaffinitize-element.md), que especifica se há uma afinidade entre os processadores e heaps do GC do servidor.</span><span class="sxs-lookup"><span data-stu-id="a6777-141">[GCNoAffinitize](gcnoaffinitize-element.md), which specifies whether there is an affinity between server GC heaps and processors.</span></span> <span data-ttu-id="a6777-142">Por padrão, há um heap GC de servidor para cada processador.</span><span class="sxs-lookup"><span data-stu-id="a6777-142">By default, there is one server GC heap for each processor.</span></span>

- <span data-ttu-id="a6777-143">[GCHeapCount](gcheapcount-element.md), que limita o número de heaps usados por um processo.</span><span class="sxs-lookup"><span data-stu-id="a6777-143">[GCHeapCount](gcheapcount-element.md), which limits the number of heaps used by a process.</span></span>

- <span data-ttu-id="a6777-144">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), que define a afinidade entre as pilhas de GC do servidor disponíveis e os processadores individuais.</span><span class="sxs-lookup"><span data-stu-id="a6777-144">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), which defines the affinity between the available server GC heaps and individual processors.</span></span>

## <a name="example"></a><span data-ttu-id="a6777-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a6777-145">Example</span></span>

<span data-ttu-id="a6777-146">O exemplo a seguir habilita a coleta de lixo do servidor:</span><span class="sxs-lookup"><span data-stu-id="a6777-146">The following example enables server garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="a6777-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6777-147">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a6777-148">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="a6777-148">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a6777-149">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="a6777-149">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a6777-150">Para desabilitar a coleta de lixo simultânea</span><span class="sxs-lookup"><span data-stu-id="a6777-150">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
