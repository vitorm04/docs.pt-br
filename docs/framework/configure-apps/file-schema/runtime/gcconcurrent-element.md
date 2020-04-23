---
title: elemento gcConcurrent
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
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102899"
---
# <a name="gcconcurrent-element"></a><span data-ttu-id="f1c28-102">\<gcElemento> concomitante</span><span class="sxs-lookup"><span data-stu-id="f1c28-102">\<gcConcurrent> element</span></span>

<span data-ttu-id="f1c28-103">Especifica se o tempo de execução do idioma comum executa a coleta de lixo em um segmento separado.</span><span class="sxs-lookup"><span data-stu-id="f1c28-103">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>

<span data-ttu-id="f1c28-104">[\<>de configuração](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f1c28-104">[\<configuration>](../configuration-element.md)</span></span>\
<span data-ttu-id="f1c28-105">&nbsp;&nbsp;[\<>de tempo de execução](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="f1c28-105">&nbsp;&nbsp;[\<runtime>](runtime-element.md)</span></span>\
<span data-ttu-id="f1c28-106">&nbsp;&nbsp;&nbsp;&nbsp;\<> gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="f1c28-106">&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent></span></span>

## <a name="syntax"></a><span data-ttu-id="f1c28-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f1c28-107">Syntax</span></span>

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f1c28-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f1c28-108">Attributes and elements</span></span>

<span data-ttu-id="f1c28-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f1c28-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f1c28-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="f1c28-110">Attributes</span></span>

|<span data-ttu-id="f1c28-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="f1c28-111">Attribute</span></span>|<span data-ttu-id="f1c28-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1c28-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="f1c28-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="f1c28-113">Required attribute.</span></span><br /><br /><span data-ttu-id="f1c28-114">Especifica se o runtime executa a coleta de lixo simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="f1c28-114">Specifies whether the runtime runs garbage collection concurrently.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="f1c28-115">atributo ativado</span><span class="sxs-lookup"><span data-stu-id="f1c28-115">enabled attribute</span></span>

|<span data-ttu-id="f1c28-116">Valor</span><span class="sxs-lookup"><span data-stu-id="f1c28-116">Value</span></span>|<span data-ttu-id="f1c28-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1c28-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="f1c28-118">Não funciona a coleta de lixo simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="f1c28-118">Doesn't run garbage collection concurrently.</span></span>|
|`true`|<span data-ttu-id="f1c28-119">Executa a coleta de lixo simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="f1c28-119">Runs garbage collection concurrently.</span></span> <span data-ttu-id="f1c28-120">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="f1c28-120">This is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="f1c28-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f1c28-121">Child elements</span></span>

<span data-ttu-id="f1c28-122">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f1c28-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f1c28-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f1c28-123">Parent elements</span></span>

|<span data-ttu-id="f1c28-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="f1c28-124">Element</span></span>|<span data-ttu-id="f1c28-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1c28-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="f1c28-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f1c28-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="f1c28-127">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="f1c28-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f1c28-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="f1c28-128">Remarks</span></span>

<span data-ttu-id="f1c28-129">Antes do .NET Framework 4, a coleta de lixo da estação de trabalho suportava a coleta simultânea de lixo, que realizava a coleta de lixo em segundo plano em um fio separado.</span><span class="sxs-lookup"><span data-stu-id="f1c28-129">Prior to .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="f1c28-130">No Framework 4 ,NET Framework 4, a coleta simultânea de lixo foi substituída pelo GC de fundo, que também realiza a coleta de lixo em segundo plano em um segmento separado.</span><span class="sxs-lookup"><span data-stu-id="f1c28-130">In .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="f1c28-131">A partir do .NET Framework 4.5, a coleta de fundos tornou-se disponível na coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="f1c28-131">Starting with .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="f1c28-132">O elemento **gcConcurrent controla** se o tempo de execução realiza a coleta de lixo simultânea ou em segundo plano, se está disponível ou se realiza a coleta de lixo em primeiro plano.</span><span class="sxs-lookup"><span data-stu-id="f1c28-132">The **gcConcurrent** element controls whether the runtime performs either concurrent or background garbage collection, if it's available, or whether it performs garbage collection in the foreground.</span></span>

### <a name="to-disable-background-garbage-collection"></a><span data-ttu-id="f1c28-133">Para desativar a coleta de lixo em segundo plano</span><span class="sxs-lookup"><span data-stu-id="f1c28-133">To disable background garbage collection</span></span>

> [!WARNING]
> <span data-ttu-id="f1c28-134">A partir do Framework 4 .NET, a coleta simultânea de lixo é substituída pela coleta de lixo de fundo.</span><span class="sxs-lookup"><span data-stu-id="f1c28-134">Starting with .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="f1c28-135">Os termos *simultâneos* e *de fundo* são usados de forma intercambiável na documentação .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f1c28-135">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="f1c28-136">Para desativar a coleta de lixo de fundo, utilize o elemento **gcConcurrent,** conforme discutido neste artigo.</span><span class="sxs-lookup"><span data-stu-id="f1c28-136">To disable background garbage collection, use the **gcConcurrent** element, as discussed in this article.</span></span>

<span data-ttu-id="f1c28-137">Por padrão, o tempo de execução usa coleta de lixo simultânea ou em segundo plano, que é otimizada para latência.</span><span class="sxs-lookup"><span data-stu-id="f1c28-137">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="f1c28-138">Se o aplicativo envolver uma forte interação do usuário, deixe a coleta de lixo simultânea habilitada a minimizar o tempo de pausa do aplicativo para realizar a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="f1c28-138">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="f1c28-139">Se você `enabled` definir o atributo do `false`elemento **gcConcurrent** para , o tempo de execução usará a coleta de lixo não simultânea, que é otimizada para throughput.</span><span class="sxs-lookup"><span data-stu-id="f1c28-139">If you set the `enabled` attribute of the **gcConcurrent** element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span>

<span data-ttu-id="f1c28-140">O arquivo de configuração a seguir desativa a coleta de lixo em segundo plano:</span><span class="sxs-lookup"><span data-stu-id="f1c28-140">The following configuration file disables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

<span data-ttu-id="f1c28-141">Se houver uma configuração **gcConcurrentSetting** no arquivo de configuração da máquina, ele definirá o valor padrão para todos os aplicativos .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f1c28-141">If there's a **gcConcurrentSetting** setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="f1c28-142">A configuração do arquivo de configuração da máquina substitui a configuração de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f1c28-142">The machine configuration file setting overrides the application configuration file setting.</span></span>

<span data-ttu-id="f1c28-143">Para obter mais informações sobre coleta de lixo simultânea e de fundo, consulte [Coleta de lixo em segundo plano](../../../../standard/garbage-collection/background-gc.md).</span><span class="sxs-lookup"><span data-stu-id="f1c28-143">For more information on concurrent and background garbage collection, see [Background garbage collection](../../../../standard/garbage-collection/background-gc.md).</span></span>

## <a name="example"></a><span data-ttu-id="f1c28-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f1c28-144">Example</span></span>

<span data-ttu-id="f1c28-145">O exemplo a seguir permite a coleta de lixo em segundo plano:</span><span class="sxs-lookup"><span data-stu-id="f1c28-145">The following example enables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="f1c28-146">Confira também</span><span class="sxs-lookup"><span data-stu-id="f1c28-146">See also</span></span>

- [<span data-ttu-id="f1c28-147">Esquema de configurações em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="f1c28-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f1c28-148">Esquema de arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="f1c28-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="f1c28-149">Noções básicas sobre a coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="f1c28-149">Fundamentals of Garbage Collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
