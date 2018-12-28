---
title: '&lt;gcServer&gt; Element'
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
ms.openlocfilehash: 80421a66a3ace4970324fb295e167b7d4875063f
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610666"
---
# <a name="ltgcservergt-element"></a><span data-ttu-id="bbe2e-102">&lt;gcServer&gt; Element</span><span class="sxs-lookup"><span data-stu-id="bbe2e-102">&lt;gcServer&gt; Element</span></span>
<span data-ttu-id="bbe2e-103">Especifica se o Common Language Runtime executa a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="bbe2e-103">Specifies whether the common language runtime runs server garbage collection.</span></span>  
  
 <span data-ttu-id="bbe2e-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="bbe2e-104">\<configuration></span></span>  
<span data-ttu-id="bbe2e-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="bbe2e-105">\<runtime></span></span>  
<span data-ttu-id="bbe2e-106">\<gcServer></span><span class="sxs-lookup"><span data-stu-id="bbe2e-106">\<gcServer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbe2e-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bbe2e-107">Syntax</span></span>  
  
```xml  
<gcServer    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bbe2e-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bbe2e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="bbe2e-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bbe2e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bbe2e-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="bbe2e-110">Attributes</span></span>  
  
|<span data-ttu-id="bbe2e-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="bbe2e-111">Attribute</span></span>|<span data-ttu-id="bbe2e-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="bbe2e-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="bbe2e-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="bbe2e-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="bbe2e-114">Especifica se o tempo de execução executa a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="bbe2e-114">Specifies whether the runtime runs server garbage collection.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="bbe2e-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="bbe2e-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="bbe2e-116">Valor</span><span class="sxs-lookup"><span data-stu-id="bbe2e-116">Value</span></span>|<span data-ttu-id="bbe2e-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="bbe2e-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="bbe2e-118">Não é executado a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="bbe2e-118">Does not run server garbage collection.</span></span> <span data-ttu-id="bbe2e-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="bbe2e-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="bbe2e-120">Executa a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="bbe2e-120">Runs server garbage collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bbe2e-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bbe2e-121">Child Elements</span></span>  
 <span data-ttu-id="bbe2e-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="bbe2e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bbe2e-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bbe2e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="bbe2e-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="bbe2e-124">Element</span></span>|<span data-ttu-id="bbe2e-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="bbe2e-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bbe2e-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bbe2e-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="bbe2e-127">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="bbe2e-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bbe2e-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="bbe2e-128">Remarks</span></span>  
 <span data-ttu-id="bbe2e-129">O common language runtime (CLR) dá suporte a dois tipos de coleta de lixo: coleta de lixo de estação de trabalho, que está disponível em todos os sistemas, e coleta de lixo do servidor, que está disponível em sistemas multiprocessadores.</span><span class="sxs-lookup"><span data-stu-id="bbe2e-129">The common language runtime (CLR) supports two types of garbage collection: workstation garbage collection, which is available on all systems, and server garbage collection, which is available on multiprocessor systems.</span></span> <span data-ttu-id="bbe2e-130">Você usa o `<gcServer>` elemento para controlar o tipo de coleta de lixo do CLR executa.</span><span class="sxs-lookup"><span data-stu-id="bbe2e-130">You use the `<gcServer>` element to control the type of garbage collection the CLR performs.</span></span> <span data-ttu-id="bbe2e-131">Use o <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> propriedade para determinar se a coleta de lixo do servidor está habilitada.</span><span class="sxs-lookup"><span data-stu-id="bbe2e-131">Use the <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> property to determine if server garbage collection is enabled.</span></span>  
  
 <span data-ttu-id="bbe2e-132">Para computadores com processador único, a coleta de lixo de estação de trabalho padrão deve ser a opção mais rápida.</span><span class="sxs-lookup"><span data-stu-id="bbe2e-132">For single-processor computers, the default workstation garbage collection should be the fastest option.</span></span> <span data-ttu-id="bbe2e-133">Estação de trabalho ou servidor pode ser usado para computadores com dois processadores.</span><span class="sxs-lookup"><span data-stu-id="bbe2e-133">Either workstation or server can be used for two-processor computers.</span></span> <span data-ttu-id="bbe2e-134">Coleta de lixo do servidor deve ser a opção mais rápida para mais de dois processadores.</span><span class="sxs-lookup"><span data-stu-id="bbe2e-134">Server garbage collection should be the fastest option for more than two processors.</span></span>  
  
 <span data-ttu-id="bbe2e-135">Esse elemento pode ser usado apenas no arquivo de configuração do aplicativo; ele será ignorado se for no arquivo de configuração do computador.</span><span class="sxs-lookup"><span data-stu-id="bbe2e-135">This element can be used only in the application configuration file; it is ignored if it is in the machine configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bbe2e-136">No .NET Framework 4 e versões anteriores, coleta de lixo simultânea não está disponível quando a coleta de lixo do servidor está habilitada.</span><span class="sxs-lookup"><span data-stu-id="bbe2e-136">In the .NET Framework 4 and earlier versions, concurrent garbage collection is not available when server garbage collection is enabled.</span></span> <span data-ttu-id="bbe2e-137">Começando com o [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], coleta de lixo do servidor é simultânea.</span><span class="sxs-lookup"><span data-stu-id="bbe2e-137">Starting with the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], server garbage collection is concurrent.</span></span> <span data-ttu-id="bbe2e-138">Para usar a coleta de lixo não simultânea server, defina as `<gcServer>` elemento a ser `true` e o [ \<gcConcurrent > elemento](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) para `false`.</span><span class="sxs-lookup"><span data-stu-id="bbe2e-138">To use non-concurrent server garbage collection, set the `<gcServer>` element to `true` and the [\<gcConcurrent> element](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbe2e-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bbe2e-139">Example</span></span>  
 <span data-ttu-id="bbe2e-140">O exemplo a seguir habilita a coleta de lixo de servidor.</span><span class="sxs-lookup"><span data-stu-id="bbe2e-140">The following example enables server garbage collection.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bbe2e-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bbe2e-141">See Also</span></span>  
- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="bbe2e-142">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="bbe2e-142">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [<span data-ttu-id="bbe2e-143">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="bbe2e-143">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="bbe2e-144">Como: Desabilitar a coleta de lixo simultânea</span><span class="sxs-lookup"><span data-stu-id="bbe2e-144">How to: Disable Concurrent Garbage Collection</span></span>](https://msdn.microsoft.com/library/ba2c6c67-5778-497c-9fac-5f793b5500c7)
