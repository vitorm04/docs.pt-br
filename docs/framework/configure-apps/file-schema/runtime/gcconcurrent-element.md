---
title: Elemento gcConcurrent
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
ms.openlocfilehash: 5957337aa960a0d5f445249b410dbfaddb7b08e9
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73969227"
---
# <a name="gcconcurrent-element"></a><span data-ttu-id="2b6f3-102">\<elemento de > gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="2b6f3-102">\<gcConcurrent> element</span></span>

<span data-ttu-id="2b6f3-103">Especifica se o Common Language Runtime executa a coleta de lixo em um thread separado.</span><span class="sxs-lookup"><span data-stu-id="2b6f3-103">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>

<span data-ttu-id="2b6f3-104">[\<configuration>](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2b6f3-104">[\<configuration>](../configuration-element.md)</span></span>\
<span data-ttu-id="2b6f3-105">> &nbsp;de [\<de tempo de execução](runtime-element.md) do &nbsp;</span><span class="sxs-lookup"><span data-stu-id="2b6f3-105">&nbsp;&nbsp;[\<runtime>](runtime-element.md)</span></span>\
<span data-ttu-id="2b6f3-106">&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent ></span><span class="sxs-lookup"><span data-stu-id="2b6f3-106">&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent></span></span>

## <a name="syntax"></a><span data-ttu-id="2b6f3-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2b6f3-107">Syntax</span></span>

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2b6f3-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2b6f3-108">Attributes and elements</span></span>

<span data-ttu-id="2b6f3-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2b6f3-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="2b6f3-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="2b6f3-110">Attributes</span></span>

|<span data-ttu-id="2b6f3-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="2b6f3-111">Attribute</span></span>|<span data-ttu-id="2b6f3-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b6f3-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="2b6f3-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="2b6f3-113">Required attribute.</span></span><br /><br /><span data-ttu-id="2b6f3-114">Especifica se o runtime executa a coleta de lixo simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="2b6f3-114">Specifies whether the runtime runs garbage collection concurrently.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="2b6f3-115">atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="2b6f3-115">enabled attribute</span></span>

|<span data-ttu-id="2b6f3-116">Valor</span><span class="sxs-lookup"><span data-stu-id="2b6f3-116">Value</span></span>|<span data-ttu-id="2b6f3-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b6f3-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="2b6f3-118">Não executa a coleta de lixo simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="2b6f3-118">Doesn't run garbage collection concurrently.</span></span>|
|`true`|<span data-ttu-id="2b6f3-119">Executa a coleta de lixo simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="2b6f3-119">Runs garbage collection concurrently.</span></span> <span data-ttu-id="2b6f3-120">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="2b6f3-120">This is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="2b6f3-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2b6f3-121">Child elements</span></span>

<span data-ttu-id="2b6f3-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="2b6f3-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2b6f3-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2b6f3-123">Parent elements</span></span>

|<span data-ttu-id="2b6f3-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="2b6f3-124">Element</span></span>|<span data-ttu-id="2b6f3-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b6f3-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="2b6f3-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2b6f3-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="2b6f3-127">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="2b6f3-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2b6f3-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="2b6f3-128">Remarks</span></span>

<span data-ttu-id="2b6f3-129">Antes do .NET Framework 4, a coleta de lixo da estação de trabalho oferecia suporte à coleta de lixo simultânea, que realizou a coleta de lixo em segundo plano em um thread separado.</span><span class="sxs-lookup"><span data-stu-id="2b6f3-129">Prior to .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="2b6f3-130">No .NET Framework 4, a coleta de lixo simultânea foi substituída pelo GC em segundo plano, que também executa a coleta de lixo em segundo plano em um thread separado.</span><span class="sxs-lookup"><span data-stu-id="2b6f3-130">In .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="2b6f3-131">A partir do .NET Framework 4,5, a coleção em segundo plano tornou-se disponível na coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="2b6f3-131">Starting with .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="2b6f3-132">O elemento **gcConcurrent** controla se o tempo de execução executa uma coleta de lixo simultânea ou em segundo plano, se estiver disponível, ou se ele executará a coleta de lixo em primeiro plano.</span><span class="sxs-lookup"><span data-stu-id="2b6f3-132">The **gcConcurrent** element controls whether the runtime performs either concurrent or background garbage collection, if it's available, or whether it performs garbage collection in the foreground.</span></span>

### <a name="to-disable-background-garbage-collection"></a><span data-ttu-id="2b6f3-133">Para desabilitar a coleta de lixo em segundo plano</span><span class="sxs-lookup"><span data-stu-id="2b6f3-133">To disable background garbage collection</span></span>

> [!WARNING]
> <span data-ttu-id="2b6f3-134">A partir do .NET Framework 4, a coleta de lixo simultânea é substituída pela coleta de lixo em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="2b6f3-134">Starting with .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="2b6f3-135">Os termos *simultâneos* e de *plano de fundo* são usados de maneira intercambiável na documentação do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2b6f3-135">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="2b6f3-136">Para desabilitar a coleta de lixo em segundo plano, use o elemento **gcConcurrent** , conforme discutido neste artigo.</span><span class="sxs-lookup"><span data-stu-id="2b6f3-136">To disable background garbage collection, use the **gcConcurrent** element, as discussed in this article.</span></span>

<span data-ttu-id="2b6f3-137">Por padrão, o tempo de execução usa a coleta de lixo simultânea ou em segundo plano, que é otimizada para latência.</span><span class="sxs-lookup"><span data-stu-id="2b6f3-137">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="2b6f3-138">Se seu aplicativo envolver uma interação pesada do usuário, deixe a coleta de lixo simultânea habilitada para minimizar o tempo de pausa do aplicativo para executar a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="2b6f3-138">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="2b6f3-139">Se você definir o atributo `enabled` do elemento **gcConcurrent** como `false`, o tempo de execução usará a coleta de lixo não simultânea, que é otimizada para taxa de transferência.</span><span class="sxs-lookup"><span data-stu-id="2b6f3-139">If you set the `enabled` attribute of the **gcConcurrent** element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span>

<span data-ttu-id="2b6f3-140">O seguinte arquivo de configuração desabilita a coleta de lixo em segundo plano:</span><span class="sxs-lookup"><span data-stu-id="2b6f3-140">The following configuration file disables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

<span data-ttu-id="2b6f3-141">Se houver uma configuração **gcConcurrentSetting** no arquivo de configuração da máquina, ele definirá o valor padrão para todos os aplicativos .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2b6f3-141">If there's a **gcConcurrentSetting** setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="2b6f3-142">A configuração do arquivo de configuração do computador substitui a configuração do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2b6f3-142">The machine configuration file setting overrides the application configuration file setting.</span></span>

<span data-ttu-id="2b6f3-143">Para obter mais informações sobre coletas de lixo simultâneas e em segundo plano, consulte as seções [coleta de lixo](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection), coleta de lixo da estação de [trabalho em segundo](../../../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection)plano e coleta de lixo do servidor em [segundo plano](../../../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection) no artigo [conceitos básicos do coletor de lixo](../../../../standard/garbage-collection/fundamentals.md) .</span><span class="sxs-lookup"><span data-stu-id="2b6f3-143">For more information on concurrent and background garbage collection, see the [Concurrent garbage collection](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection), [Background workstation garbage collection](../../../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection), and [Background server garbage collection](../../../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection) sections in the [Fundamentals of Garbage Collection](../../../../standard/garbage-collection/fundamentals.md) article.</span></span>

## <a name="example"></a><span data-ttu-id="2b6f3-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b6f3-144">Example</span></span>

<span data-ttu-id="2b6f3-145">O exemplo a seguir habilita a coleta de lixo em segundo plano:</span><span class="sxs-lookup"><span data-stu-id="2b6f3-145">The following example enables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="2b6f3-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b6f3-146">See also</span></span>

- [<span data-ttu-id="2b6f3-147">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="2b6f3-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2b6f3-148">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="2b6f3-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="2b6f3-149">Conceitos básicos da coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="2b6f3-149">Fundamentals of Garbage Collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
