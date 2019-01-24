---
title: '&lt;gcConcurrent&gt; elemento'
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
ms.openlocfilehash: 4c83576c5c46d9a32f990d23fa20b116be36e4c0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611989"
---
# <a name="ltgcconcurrentgt-element"></a><span data-ttu-id="de865-102">&lt;gcConcurrent&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="de865-102">&lt;gcConcurrent&gt; Element</span></span>
<span data-ttu-id="de865-103">Especifica se o common language runtime executa a coleta de lixo em um thread separado.</span><span class="sxs-lookup"><span data-stu-id="de865-103">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>  
  
 <span data-ttu-id="de865-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="de865-104">\<configuration></span></span>  
<span data-ttu-id="de865-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="de865-105">\<runtime></span></span>  
<span data-ttu-id="de865-106">\<gcConcurrent></span><span class="sxs-lookup"><span data-stu-id="de865-106">\<gcConcurrent></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de865-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="de865-107">Syntax</span></span>  
  
```xml  
<gcConcurrent    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de865-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="de865-108">Attributes and Elements</span></span>  
 <span data-ttu-id="de865-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="de865-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de865-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="de865-110">Attributes</span></span>  
  
|<span data-ttu-id="de865-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="de865-111">Attribute</span></span>|<span data-ttu-id="de865-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="de865-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="de865-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="de865-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="de865-114">Especifica se o tempo de execução executa a coleta de lixo simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="de865-114">Specifies whether the runtime runs garbage collection concurrently.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="de865-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="de865-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="de865-116">Valor</span><span class="sxs-lookup"><span data-stu-id="de865-116">Value</span></span>|<span data-ttu-id="de865-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="de865-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="de865-118">Não executa a coleta de lixo simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="de865-118">Does not run garbage collection concurrently.</span></span>|  
|`true`|<span data-ttu-id="de865-119">Executa a coleta de lixo simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="de865-119">Runs garbage collection concurrently.</span></span> <span data-ttu-id="de865-120">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="de865-120">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de865-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="de865-121">Child Elements</span></span>  
 <span data-ttu-id="de865-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="de865-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="de865-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="de865-123">Parent Elements</span></span>  
  
|<span data-ttu-id="de865-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="de865-124">Element</span></span>|<span data-ttu-id="de865-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="de865-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="de865-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="de865-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="de865-127">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="de865-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de865-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="de865-128">Remarks</span></span>  
 <span data-ttu-id="de865-129">Antes do .NET Framework 4, coleta de lixo de estação de trabalho com suporte a coleta de lixo simultânea, o que é executada a coleta de lixo em segundo plano em um thread separado.</span><span class="sxs-lookup"><span data-stu-id="de865-129">Prior to the .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="de865-130">No .NET Framework 4, a coleta de lixo simultânea foi substituída pelo GC, que também executa a coleta de lixo em segundo plano em um thread separado em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="de865-130">In the .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="de865-131">Começando com o .NET Framework 4.5, a coleta em segundo plano foram disponibilizada na coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="de865-131">Starting with the .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="de865-132">O `<gcConcurrent>` elemento controla se o tempo de execução executa qualquer simultânea ou em segundo plano coleta de lixo, se ele estiver disponível, ou se ele executa a coleta de lixo em primeiro plano.</span><span class="sxs-lookup"><span data-stu-id="de865-132">The `<gcConcurrent>` element controls whether the runtime performs either concurrent or background garbage collection, if it is available, or whether it performs garbage collection in the foreground.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="de865-133">Começando com o .NET Framework 4, a coleta de lixo simultânea é substituída pela coleta de lixo em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="de865-133">Starting with the .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="de865-134">Os termos *simultâneas* e *plano de fundo* são usados alternadamente na documentação do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="de865-134">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="de865-135">Para desabilitar a coleta de lixo em segundo plano, use o `<gcConcurrent>` elemento, conforme discutido neste artigo.</span><span class="sxs-lookup"><span data-stu-id="de865-135">To disable background garbage collection, use the `<gcConcurrent>` element, as discussed in this article.</span></span>  
  
 <span data-ttu-id="de865-136">Por padrão, o tempo de execução usa simultâneos ou a coleta de lixo em segundo plano, que é otimizado para latência.</span><span class="sxs-lookup"><span data-stu-id="de865-136">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="de865-137">Se seu aplicativo envolve a interação do usuário pesado, deixe a coleta de lixo simultânea habilitada para minimizar o tempo de pausa do aplicativo para executar a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="de865-137">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="de865-138">Se você definir a `enabled` atributo o `<gcConcurrent>` elemento a ser `false`, o tempo de execução usa a coleta de lixo não simultânea, que é otimizada para taxa de transferência.</span><span class="sxs-lookup"><span data-stu-id="de865-138">If you set the `enabled` attribute of the `<gcConcurrent>` element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span> <span data-ttu-id="de865-139">O arquivo de configuração a seguir desabilita a coleta de lixo em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="de865-139">The following configuration file disables background garbage collection.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <gcConcurrent enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="de865-140">Se não houver um `<gcConcurrentSetting>` configuração no arquivo de configuração do computador, ele define o valor padrão para todos os aplicativos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="de865-140">If there is a `<gcConcurrentSetting>` setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="de865-141">O arquivo de configuração de máquina substitui o arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="de865-141">The machine configuration file setting overrides the application configuration file setting.</span></span>  
  
 <span data-ttu-id="de865-142">Para obter mais informações sobre simultâneas e coleta de lixo em segundo plano, consulte a seção "coleta de lixo simultânea" a [conceitos básicos da coleta de lixo](../../../../../docs/standard/garbage-collection/fundamentals.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="de865-142">For more information on concurrent and background garbage collection, see the "Concurrent garbage collection" section in the [Fundamentals of Garbage Collection](../../../../../docs/standard/garbage-collection/fundamentals.md) topic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de865-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="de865-143">Example</span></span>  
 <span data-ttu-id="de865-144">O exemplo a seguir habilita a coleta de lixo simultânea.</span><span class="sxs-lookup"><span data-stu-id="de865-144">The following example enables concurrent garbage collection.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <gcConcurrent enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="de865-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="de865-145">See also</span></span>
- [<span data-ttu-id="de865-146">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="de865-146">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="de865-147">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="de865-147">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="de865-148">Conceitos básicos da coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="de865-148">Fundamentals of Garbage Collection</span></span>](../../../../../docs/standard/garbage-collection/fundamentals.md)
