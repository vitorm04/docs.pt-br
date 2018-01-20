---
title: '&lt;GCCpuGroup&gt; Element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dcead28d7bf66e0626a0108015add4f22c5fa476
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="ltgccpugroupgt-element"></a><span data-ttu-id="241cb-102">&lt;GCCpuGroup&gt; Element</span><span class="sxs-lookup"><span data-stu-id="241cb-102">&lt;GCCpuGroup&gt; Element</span></span>
<span data-ttu-id="241cb-103">Especifica se a coleta de lixo oferece suporte a vários grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="241cb-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>  
  
 <span data-ttu-id="241cb-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="241cb-104">\<configuration></span></span>  
<span data-ttu-id="241cb-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="241cb-105">\<runtime></span></span>  
<span data-ttu-id="241cb-106">\<GCCpuGroup></span><span class="sxs-lookup"><span data-stu-id="241cb-106">\<GCCpuGroup></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="241cb-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="241cb-107">Syntax</span></span>  
  
```xml  
<GCCpuGroup    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="241cb-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="241cb-108">Attributes and Elements</span></span>  
 <span data-ttu-id="241cb-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="241cb-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="241cb-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="241cb-110">Attributes</span></span>  
  
|<span data-ttu-id="241cb-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="241cb-111">Attribute</span></span>|<span data-ttu-id="241cb-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="241cb-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="241cb-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="241cb-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="241cb-114">Especifica se a coleta de lixo oferece suporte a vários grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="241cb-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="241cb-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="241cb-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="241cb-116">Valor</span><span class="sxs-lookup"><span data-stu-id="241cb-116">Value</span></span>|<span data-ttu-id="241cb-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="241cb-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="241cb-118">Coleta de lixo não oferece suporte a vários grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="241cb-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="241cb-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="241cb-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="241cb-120">Coleta de lixo oferece suporte a vários grupos de CPU, se a coleta de lixo do servidor está habilitada.</span><span class="sxs-lookup"><span data-stu-id="241cb-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="241cb-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="241cb-121">Child Elements</span></span>  
 <span data-ttu-id="241cb-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="241cb-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="241cb-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="241cb-123">Parent Elements</span></span>  
  
|<span data-ttu-id="241cb-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="241cb-124">Element</span></span>|<span data-ttu-id="241cb-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="241cb-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="241cb-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="241cb-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="241cb-127">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="241cb-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="241cb-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="241cb-128">Remarks</span></span>  
 <span data-ttu-id="241cb-129">Quando um computador tiver vários grupos de CPU e coleta de lixo do servidor está habilitada (consulte o [ \<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) elemento), permitindo que esse elemento estende a coleta de lixo em todos os grupos de CPU e usa todos os núcleos em conta durante a criação e balanceamento heaps.</span><span class="sxs-lookup"><span data-stu-id="241cb-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="241cb-130">Esse elemento só se aplica a threads de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="241cb-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="241cb-131">Para habilitar o tempo de execução distribuir os threads de usuário em todos os grupos de CPU, você também deve habilitar o [< Thread_UseAllCpuGroups >](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="241cb-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="241cb-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="241cb-132">Example</span></span>  
 <span data-ttu-id="241cb-133">O exemplo a seguir mostra como habilitar a coleta de lixo para vários grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="241cb-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="241cb-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="241cb-134">See Also</span></span>  
 [<span data-ttu-id="241cb-135">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="241cb-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="241cb-136">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="241cb-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="241cb-137">Como: desabilitar a coleta de lixo simultânea</span><span class="sxs-lookup"><span data-stu-id="241cb-137">How to: Disable Concurrent Garbage Collection</span></span>](http://msdn.microsoft.com/library/ba2c6c67-5778-497c-9fac-5f793b5500c7)  
 [<span data-ttu-id="241cb-138">Coleta de lixo de estação de trabalho e servidor</span><span class="sxs-lookup"><span data-stu-id="241cb-138">Workstation and server garbage collection</span></span>](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
