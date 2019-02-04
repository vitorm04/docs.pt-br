---
title: Elemento <gcConcurrent>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e2be4d9384f1e1ef73ce6064184aa2621a517a8
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674588"
---
# <a name="gcconcurrent-element"></a><span data-ttu-id="8bf10-102">\<gcConcurrent > elemento</span><span class="sxs-lookup"><span data-stu-id="8bf10-102">\<gcConcurrent> Element</span></span>

<span data-ttu-id="8bf10-103">Especifica se o common language runtime executa a coleta de lixo em um thread separado.</span><span class="sxs-lookup"><span data-stu-id="8bf10-103">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>

<span data-ttu-id="8bf10-104">\<configuration>\\</span><span class="sxs-lookup"><span data-stu-id="8bf10-104">\<configuration>\\</span></span>
<span data-ttu-id="8bf10-105">\<runtime>\\</span><span class="sxs-lookup"><span data-stu-id="8bf10-105">\<runtime>\\</span></span>
<span data-ttu-id="8bf10-106">\<gcConcurrent></span><span class="sxs-lookup"><span data-stu-id="8bf10-106">\<gcConcurrent></span></span>

## <a name="syntax"></a><span data-ttu-id="8bf10-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8bf10-107">Syntax</span></span>

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8bf10-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8bf10-108">Attributes and elements</span></span>

<span data-ttu-id="8bf10-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8bf10-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8bf10-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="8bf10-110">Attributes</span></span>

|<span data-ttu-id="8bf10-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="8bf10-111">Attribute</span></span>|<span data-ttu-id="8bf10-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="8bf10-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="8bf10-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="8bf10-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="8bf10-114">Especifica se o tempo de execução executa a coleta de lixo simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="8bf10-114">Specifies whether the runtime runs garbage collection concurrently.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="8bf10-115">atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="8bf10-115">enabled attribute</span></span>

|<span data-ttu-id="8bf10-116">Valor</span><span class="sxs-lookup"><span data-stu-id="8bf10-116">Value</span></span>|<span data-ttu-id="8bf10-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="8bf10-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="8bf10-118">Não executa a coleta de lixo simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="8bf10-118">Doesn't run garbage collection concurrently.</span></span>|
|`true`|<span data-ttu-id="8bf10-119">Executa a coleta de lixo simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="8bf10-119">Runs garbage collection concurrently.</span></span> <span data-ttu-id="8bf10-120">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="8bf10-120">This is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="8bf10-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8bf10-121">Child elements</span></span>

<span data-ttu-id="8bf10-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8bf10-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8bf10-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8bf10-123">Parent elements</span></span>

|<span data-ttu-id="8bf10-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="8bf10-124">Element</span></span>|<span data-ttu-id="8bf10-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="8bf10-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="8bf10-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8bf10-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="8bf10-127">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="8bf10-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8bf10-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="8bf10-128">Remarks</span></span>

<span data-ttu-id="8bf10-129">Antes do .NET Framework 4, coleta de lixo de estação de trabalho com suporte a coleta de lixo simultânea, o que é executada a coleta de lixo em segundo plano em um thread separado.</span><span class="sxs-lookup"><span data-stu-id="8bf10-129">Prior to the .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="8bf10-130">No .NET Framework 4, a coleta de lixo simultânea foi substituída pelo GC, que também executa a coleta de lixo em segundo plano em um thread separado em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="8bf10-130">In the .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="8bf10-131">Começando com o .NET Framework 4.5, a coleta em segundo plano foram disponibilizada na coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="8bf10-131">Starting with the .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="8bf10-132">O `<gcConcurrent>` elemento controla se o tempo de execução executa qualquer simultânea ou em segundo plano coleta de lixo, se ele estiver disponível, ou se ele executa a coleta de lixo em primeiro plano.</span><span class="sxs-lookup"><span data-stu-id="8bf10-132">The `<gcConcurrent>` element controls whether the runtime performs either concurrent or background garbage collection, if it's available, or whether it performs garbage collection in the foreground.</span></span>

### <a name="to-disable-background-garbage-collection"></a><span data-ttu-id="8bf10-133">Para desabilitar a coleta de lixo em segundo plano</span><span class="sxs-lookup"><span data-stu-id="8bf10-133">To disable background garbage collection</span></span>

> [!WARNING]
> <span data-ttu-id="8bf10-134">Começando com o .NET Framework 4, a coleta de lixo simultânea é substituída pela coleta de lixo em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="8bf10-134">Starting with the .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="8bf10-135">Os termos *simultâneas* e *plano de fundo* são usados alternadamente na documentação do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8bf10-135">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="8bf10-136">Para desabilitar a coleta de lixo em segundo plano, use o `<gcConcurrent>` elemento, conforme discutido neste artigo.</span><span class="sxs-lookup"><span data-stu-id="8bf10-136">To disable background garbage collection, use the `<gcConcurrent>` element, as discussed in this article.</span></span>

<span data-ttu-id="8bf10-137">Por padrão, o tempo de execução usa simultâneos ou a coleta de lixo em segundo plano, que é otimizado para latência.</span><span class="sxs-lookup"><span data-stu-id="8bf10-137">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="8bf10-138">Se seu aplicativo envolve a interação do usuário pesado, deixe a coleta de lixo simultânea habilitada para minimizar o tempo de pausa do aplicativo para executar a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="8bf10-138">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="8bf10-139">Se você definir a `enabled` atributo o `<gcConcurrent>` elemento a ser `false`, o tempo de execução usa a coleta de lixo não simultânea, que é otimizada para taxa de transferência.</span><span class="sxs-lookup"><span data-stu-id="8bf10-139">If you set the `enabled` attribute of the `<gcConcurrent>` element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span> <span data-ttu-id="8bf10-140">O arquivo de configuração a seguir desabilita a coleta de lixo em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="8bf10-140">The following configuration file disables background garbage collection.</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

 <span data-ttu-id="8bf10-141">Se não houver um `<gcConcurrentSetting>` configuração no arquivo de configuração do computador, ele define o valor padrão para todos os aplicativos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8bf10-141">If there's a `<gcConcurrentSetting>` setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="8bf10-142">O arquivo de configuração de máquina substitui o arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8bf10-142">The machine configuration file setting overrides the application configuration file setting.</span></span>

 <span data-ttu-id="8bf10-143">Para obter mais informações sobre simultâneas e coleta de lixo em segundo plano, consulte o [coleta de lixo simultânea](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection) seção o [conceitos básicos da coleta de lixo](../../../../standard/garbage-collection/fundamentals.md) artigo.</span><span class="sxs-lookup"><span data-stu-id="8bf10-143">For more information on concurrent and background garbage collection, see the [Concurrent garbage collection](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection) section in the [Fundamentals of Garbage Collection](../../../../standard/garbage-collection/fundamentals.md) article.</span></span>

## <a name="example"></a><span data-ttu-id="8bf10-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8bf10-144">Example</span></span>

<span data-ttu-id="8bf10-145">O exemplo a seguir habilita a coleta de lixo simultânea:</span><span class="sxs-lookup"><span data-stu-id="8bf10-145">The following example enables concurrent garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="8bf10-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8bf10-146">See also</span></span>

- [<span data-ttu-id="8bf10-147">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="8bf10-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="8bf10-148">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="8bf10-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="8bf10-149">Conceitos básicos da coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="8bf10-149">Fundamentals of Garbage Collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
