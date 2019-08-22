---
title: Elemento <gcServer>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 61b4076a72dbc17ffc800a1a8d37a22d1435e02b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663677"
---
# <a name="gcserver-element"></a><span data-ttu-id="0d83b-102">\<Elemento de > gcServer</span><span class="sxs-lookup"><span data-stu-id="0d83b-102">\<gcServer> Element</span></span>
<span data-ttu-id="0d83b-103">Especifica se o Common Language Runtime executa a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="0d83b-103">Specifies whether the common language runtime runs server garbage collection.</span></span>  
  
 <span data-ttu-id="0d83b-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="0d83b-104">\<configuration></span></span>  
<span data-ttu-id="0d83b-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="0d83b-105">\<runtime></span></span>  
<span data-ttu-id="0d83b-106">\<gcServer></span><span class="sxs-lookup"><span data-stu-id="0d83b-106">\<gcServer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d83b-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d83b-107">Syntax</span></span>  
  
```xml  
<gcServer    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d83b-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0d83b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0d83b-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0d83b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d83b-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="0d83b-110">Attributes</span></span>  
  
|<span data-ttu-id="0d83b-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="0d83b-111">Attribute</span></span>|<span data-ttu-id="0d83b-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d83b-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="0d83b-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="0d83b-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="0d83b-114">Especifica se o tempo de execução executa a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="0d83b-114">Specifies whether the runtime runs server garbage collection.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="0d83b-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="0d83b-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="0d83b-116">Valor</span><span class="sxs-lookup"><span data-stu-id="0d83b-116">Value</span></span>|<span data-ttu-id="0d83b-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d83b-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="0d83b-118">Não executa a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="0d83b-118">Does not run server garbage collection.</span></span> <span data-ttu-id="0d83b-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="0d83b-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="0d83b-120">Executa a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="0d83b-120">Runs server garbage collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0d83b-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0d83b-121">Child Elements</span></span>  
 <span data-ttu-id="0d83b-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0d83b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0d83b-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0d83b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="0d83b-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="0d83b-124">Element</span></span>|<span data-ttu-id="0d83b-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d83b-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0d83b-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0d83b-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="0d83b-127">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="0d83b-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d83b-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="0d83b-128">Remarks</span></span>  
 <span data-ttu-id="0d83b-129">O Common Language Runtime (CLR) dá suporte a dois tipos de coleta de lixo: coleta de lixo da estação de trabalho, que está disponível em todos os sistemas e coleta de lixo do servidor, que está disponível em sistemas de multiprocessadores.</span><span class="sxs-lookup"><span data-stu-id="0d83b-129">The common language runtime (CLR) supports two types of garbage collection: workstation garbage collection, which is available on all systems, and server garbage collection, which is available on multiprocessor systems.</span></span> <span data-ttu-id="0d83b-130">Você usa o `<gcServer>` elemento para controlar o tipo de coleta de lixo que o CLR executa.</span><span class="sxs-lookup"><span data-stu-id="0d83b-130">You use the `<gcServer>` element to control the type of garbage collection the CLR performs.</span></span> <span data-ttu-id="0d83b-131">Use a <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> propriedade para determinar se a coleta de lixo do servidor está habilitada.</span><span class="sxs-lookup"><span data-stu-id="0d83b-131">Use the <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> property to determine if server garbage collection is enabled.</span></span>  
  
 <span data-ttu-id="0d83b-132">Para computadores com um único processador, a coleta de lixo da estação de trabalho padrão deve ser a opção mais rápida.</span><span class="sxs-lookup"><span data-stu-id="0d83b-132">For single-processor computers, the default workstation garbage collection should be the fastest option.</span></span> <span data-ttu-id="0d83b-133">A estação de trabalho ou o servidor pode ser usado para computadores com dois processadores.</span><span class="sxs-lookup"><span data-stu-id="0d83b-133">Either workstation or server can be used for two-processor computers.</span></span> <span data-ttu-id="0d83b-134">A coleta de lixo do servidor deve ser a opção mais rápida para mais de dois processadores.</span><span class="sxs-lookup"><span data-stu-id="0d83b-134">Server garbage collection should be the fastest option for more than two processors.</span></span>  
  
 <span data-ttu-id="0d83b-135">Esse elemento só pode ser usado no arquivo de configuração do aplicativo; Ela será ignorada se estiver no arquivo de configuração da máquina.</span><span class="sxs-lookup"><span data-stu-id="0d83b-135">This element can be used only in the application configuration file; it is ignored if it is in the machine configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0d83b-136">No .NET Framework 4 e versões anteriores, a coleta de lixo simultânea não está disponível quando a coleta de lixo do servidor está habilitada.</span><span class="sxs-lookup"><span data-stu-id="0d83b-136">In the .NET Framework 4 and earlier versions, concurrent garbage collection is not available when server garbage collection is enabled.</span></span> <span data-ttu-id="0d83b-137">A partir do .NET Framework 4,5, a coleta de lixo do servidor é simultânea.</span><span class="sxs-lookup"><span data-stu-id="0d83b-137">Starting with the .NET Framework 4.5, server garbage collection is concurrent.</span></span> <span data-ttu-id="0d83b-138">Para usar a coleta de lixo do servidor não simultânea, defina `<gcServer>` o elemento `true` como e o [ \<elemento de > gcConcurrent](gcconcurrent-element.md) como. `false`</span><span class="sxs-lookup"><span data-stu-id="0d83b-138">To use non-concurrent server garbage collection, set the `<gcServer>` element to `true` and the [\<gcConcurrent> element](gcconcurrent-element.md) to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d83b-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0d83b-139">Example</span></span>  
 <span data-ttu-id="0d83b-140">O exemplo a seguir habilita a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="0d83b-140">The following example enables server garbage collection.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d83b-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d83b-141">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="0d83b-142">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="0d83b-142">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0d83b-143">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="0d83b-143">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="0d83b-144">Para desabilitar a coleta de lixo simultânea</span><span class="sxs-lookup"><span data-stu-id="0d83b-144">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
