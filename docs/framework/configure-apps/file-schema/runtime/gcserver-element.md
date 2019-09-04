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
ms.openlocfilehash: aa03179df1cd2595b4be428106dd3ec10b309317
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252545"
---
# <a name="gcserver-element"></a><span data-ttu-id="3b7de-102">\<Elemento de > gcServer</span><span class="sxs-lookup"><span data-stu-id="3b7de-102">\<gcServer> Element</span></span>
<span data-ttu-id="3b7de-103">Especifica se o Common Language Runtime executa a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="3b7de-103">Specifies whether the common language runtime runs server garbage collection.</span></span>  
  
<span data-ttu-id="3b7de-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3b7de-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3b7de-105">&nbsp;&nbsp;[ **\<> de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="3b7de-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="3b7de-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<gcServer>**</span><span class="sxs-lookup"><span data-stu-id="3b7de-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<gcServer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b7de-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3b7de-107">Syntax</span></span>  
  
```xml  
<gcServer    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b7de-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3b7de-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3b7de-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3b7de-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3b7de-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="3b7de-110">Attributes</span></span>  
  
|<span data-ttu-id="3b7de-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="3b7de-111">Attribute</span></span>|<span data-ttu-id="3b7de-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="3b7de-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="3b7de-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="3b7de-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="3b7de-114">Especifica se o tempo de execução executa a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="3b7de-114">Specifies whether the runtime runs server garbage collection.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="3b7de-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="3b7de-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="3b7de-116">Valor</span><span class="sxs-lookup"><span data-stu-id="3b7de-116">Value</span></span>|<span data-ttu-id="3b7de-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="3b7de-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="3b7de-118">Não executa a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="3b7de-118">Does not run server garbage collection.</span></span> <span data-ttu-id="3b7de-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="3b7de-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="3b7de-120">Executa a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="3b7de-120">Runs server garbage collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3b7de-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3b7de-121">Child Elements</span></span>  
 <span data-ttu-id="3b7de-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="3b7de-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3b7de-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3b7de-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3b7de-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="3b7de-124">Element</span></span>|<span data-ttu-id="3b7de-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="3b7de-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3b7de-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3b7de-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3b7de-127">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="3b7de-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b7de-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="3b7de-128">Remarks</span></span>  
 <span data-ttu-id="3b7de-129">O Common Language Runtime (CLR) dá suporte a dois tipos de coleta de lixo: coleta de lixo da estação de trabalho, que está disponível em todos os sistemas e coleta de lixo do servidor, que está disponível em sistemas de multiprocessadores.</span><span class="sxs-lookup"><span data-stu-id="3b7de-129">The common language runtime (CLR) supports two types of garbage collection: workstation garbage collection, which is available on all systems, and server garbage collection, which is available on multiprocessor systems.</span></span> <span data-ttu-id="3b7de-130">Você usa o `<gcServer>` elemento para controlar o tipo de coleta de lixo que o CLR executa.</span><span class="sxs-lookup"><span data-stu-id="3b7de-130">You use the `<gcServer>` element to control the type of garbage collection the CLR performs.</span></span> <span data-ttu-id="3b7de-131">Use a <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> propriedade para determinar se a coleta de lixo do servidor está habilitada.</span><span class="sxs-lookup"><span data-stu-id="3b7de-131">Use the <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> property to determine if server garbage collection is enabled.</span></span>  
  
 <span data-ttu-id="3b7de-132">Para computadores com um único processador, a coleta de lixo da estação de trabalho padrão deve ser a opção mais rápida.</span><span class="sxs-lookup"><span data-stu-id="3b7de-132">For single-processor computers, the default workstation garbage collection should be the fastest option.</span></span> <span data-ttu-id="3b7de-133">A estação de trabalho ou o servidor pode ser usado para computadores com dois processadores.</span><span class="sxs-lookup"><span data-stu-id="3b7de-133">Either workstation or server can be used for two-processor computers.</span></span> <span data-ttu-id="3b7de-134">A coleta de lixo do servidor deve ser a opção mais rápida para mais de dois processadores.</span><span class="sxs-lookup"><span data-stu-id="3b7de-134">Server garbage collection should be the fastest option for more than two processors.</span></span>  
  
 <span data-ttu-id="3b7de-135">Esse elemento só pode ser usado no arquivo de configuração do aplicativo; Ela será ignorada se estiver no arquivo de configuração da máquina.</span><span class="sxs-lookup"><span data-stu-id="3b7de-135">This element can be used only in the application configuration file; it is ignored if it is in the machine configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3b7de-136">No .NET Framework 4 e versões anteriores, a coleta de lixo simultânea não está disponível quando a coleta de lixo do servidor está habilitada.</span><span class="sxs-lookup"><span data-stu-id="3b7de-136">In the .NET Framework 4 and earlier versions, concurrent garbage collection is not available when server garbage collection is enabled.</span></span> <span data-ttu-id="3b7de-137">A partir do .NET Framework 4,5, a coleta de lixo do servidor é simultânea.</span><span class="sxs-lookup"><span data-stu-id="3b7de-137">Starting with the .NET Framework 4.5, server garbage collection is concurrent.</span></span> <span data-ttu-id="3b7de-138">Para usar a coleta de lixo do servidor não simultânea, defina `<gcServer>` o elemento `true` como e o [ \<elemento de > gcConcurrent](gcconcurrent-element.md) como. `false`</span><span class="sxs-lookup"><span data-stu-id="3b7de-138">To use non-concurrent server garbage collection, set the `<gcServer>` element to `true` and the [\<gcConcurrent> element](gcconcurrent-element.md) to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b7de-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3b7de-139">Example</span></span>  
 <span data-ttu-id="3b7de-140">O exemplo a seguir habilita a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="3b7de-140">The following example enables server garbage collection.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3b7de-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b7de-141">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="3b7de-142">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="3b7de-142">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3b7de-143">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="3b7de-143">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="3b7de-144">Para desabilitar a coleta de lixo simultânea</span><span class="sxs-lookup"><span data-stu-id="3b7de-144">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
