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
ms.openlocfilehash: 249518ae7477d284d50f9010757db83b7752c657
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "82102899"
---
# <a name="gcconcurrent-element"></a><span data-ttu-id="0c430-102">Elemento \<gcConcurrent></span><span class="sxs-lookup"><span data-stu-id="0c430-102">\<gcConcurrent> element</span></span>

<span data-ttu-id="0c430-103">Especifica se o Common Language Runtime executa a coleta de lixo em um thread separado.</span><span class="sxs-lookup"><span data-stu-id="0c430-103">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent>

## <a name="syntax"></a><span data-ttu-id="0c430-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0c430-104">Syntax</span></span>

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0c430-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0c430-105">Attributes and elements</span></span>

<span data-ttu-id="0c430-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0c430-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0c430-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="0c430-107">Attributes</span></span>

|<span data-ttu-id="0c430-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="0c430-108">Attribute</span></span>|<span data-ttu-id="0c430-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="0c430-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="0c430-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="0c430-110">Required attribute.</span></span><br /><br /><span data-ttu-id="0c430-111">Especifica se o runtime executa a coleta de lixo simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="0c430-111">Specifies whether the runtime runs garbage collection concurrently.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="0c430-112">atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="0c430-112">enabled attribute</span></span>

|<span data-ttu-id="0c430-113">Valor</span><span class="sxs-lookup"><span data-stu-id="0c430-113">Value</span></span>|<span data-ttu-id="0c430-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="0c430-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="0c430-115">Não executa a coleta de lixo simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="0c430-115">Doesn't run garbage collection concurrently.</span></span>|
|`true`|<span data-ttu-id="0c430-116">Executa a coleta de lixo simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="0c430-116">Runs garbage collection concurrently.</span></span> <span data-ttu-id="0c430-117">Este é o padrão.</span><span class="sxs-lookup"><span data-stu-id="0c430-117">This is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="0c430-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0c430-118">Child elements</span></span>

<span data-ttu-id="0c430-119">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0c430-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0c430-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0c430-120">Parent elements</span></span>

|<span data-ttu-id="0c430-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="0c430-121">Element</span></span>|<span data-ttu-id="0c430-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="0c430-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="0c430-123">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0c430-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="0c430-124">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="0c430-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0c430-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="0c430-125">Remarks</span></span>

<span data-ttu-id="0c430-126">Antes do .NET Framework 4, a coleta de lixo da estação de trabalho oferecia suporte à coleta de lixo simultânea, que realizou a coleta de lixo em segundo plano em um thread separado.</span><span class="sxs-lookup"><span data-stu-id="0c430-126">Prior to .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="0c430-127">No .NET Framework 4, a coleta de lixo simultânea foi substituída pelo GC em segundo plano, que também executa a coleta de lixo em segundo plano em um thread separado.</span><span class="sxs-lookup"><span data-stu-id="0c430-127">In .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="0c430-128">A partir do .NET Framework 4,5, a coleção em segundo plano tornou-se disponível na coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="0c430-128">Starting with .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="0c430-129">O elemento **gcConcurrent** controla se o tempo de execução executa uma coleta de lixo simultânea ou em segundo plano, se estiver disponível, ou se ele executará a coleta de lixo em primeiro plano.</span><span class="sxs-lookup"><span data-stu-id="0c430-129">The **gcConcurrent** element controls whether the runtime performs either concurrent or background garbage collection, if it's available, or whether it performs garbage collection in the foreground.</span></span>

### <a name="to-disable-background-garbage-collection"></a><span data-ttu-id="0c430-130">Para desabilitar a coleta de lixo em segundo plano</span><span class="sxs-lookup"><span data-stu-id="0c430-130">To disable background garbage collection</span></span>

> [!WARNING]
> <span data-ttu-id="0c430-131">A partir do .NET Framework 4, a coleta de lixo simultânea é substituída pela coleta de lixo em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="0c430-131">Starting with .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="0c430-132">Os termos *simultâneos* e de *plano de fundo* são usados de maneira intercambiável na documentação do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0c430-132">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="0c430-133">Para desabilitar a coleta de lixo em segundo plano, use o elemento **gcConcurrent** , conforme discutido neste artigo.</span><span class="sxs-lookup"><span data-stu-id="0c430-133">To disable background garbage collection, use the **gcConcurrent** element, as discussed in this article.</span></span>

<span data-ttu-id="0c430-134">Por padrão, o tempo de execução usa a coleta de lixo simultânea ou em segundo plano, que é otimizada para latência.</span><span class="sxs-lookup"><span data-stu-id="0c430-134">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="0c430-135">Se seu aplicativo envolver uma interação pesada do usuário, deixe a coleta de lixo simultânea habilitada para minimizar o tempo de pausa do aplicativo para executar a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="0c430-135">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="0c430-136">Se você definir o `enabled` atributo do elemento **gcConcurrent** como `false` , o tempo de execução usará a coleta de lixo não simultânea, que é otimizada para taxa de transferência.</span><span class="sxs-lookup"><span data-stu-id="0c430-136">If you set the `enabled` attribute of the **gcConcurrent** element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span>

<span data-ttu-id="0c430-137">O seguinte arquivo de configuração desabilita a coleta de lixo em segundo plano:</span><span class="sxs-lookup"><span data-stu-id="0c430-137">The following configuration file disables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

<span data-ttu-id="0c430-138">Se houver uma configuração **gcConcurrentSetting** no arquivo de configuração da máquina, ele definirá o valor padrão para todos os aplicativos .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0c430-138">If there's a **gcConcurrentSetting** setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="0c430-139">A configuração do arquivo de configuração do computador substitui a configuração do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0c430-139">The machine configuration file setting overrides the application configuration file setting.</span></span>

<span data-ttu-id="0c430-140">Para obter mais informações sobre a coleta de lixo simultânea e em segundo plano, consulte [coleta de lixo em segundo plano](../../../../standard/garbage-collection/background-gc.md).</span><span class="sxs-lookup"><span data-stu-id="0c430-140">For more information on concurrent and background garbage collection, see [Background garbage collection](../../../../standard/garbage-collection/background-gc.md).</span></span>

## <a name="example"></a><span data-ttu-id="0c430-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0c430-141">Example</span></span>

<span data-ttu-id="0c430-142">O exemplo a seguir habilita a coleta de lixo em segundo plano:</span><span class="sxs-lookup"><span data-stu-id="0c430-142">The following example enables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="0c430-143">Confira também</span><span class="sxs-lookup"><span data-stu-id="0c430-143">See also</span></span>

- [<span data-ttu-id="0c430-144">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="0c430-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0c430-145">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="0c430-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="0c430-146">Noções básicas sobre a coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="0c430-146">Fundamentals of Garbage Collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
