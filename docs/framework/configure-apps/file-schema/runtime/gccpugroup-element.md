---
title: Elemento <GCCpuGroup>
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85cfe57f7a3b8cfecfae4c4ae00efaea464e6120
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674084"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="92a1e-102">\<GCCpuGroup > elemento</span><span class="sxs-lookup"><span data-stu-id="92a1e-102">\<GCCpuGroup> Element</span></span>
<span data-ttu-id="92a1e-103">Especifica se a coleta de lixo oferece suporte a vários grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="92a1e-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>  
  
 <span data-ttu-id="92a1e-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="92a1e-104">\<configuration></span></span>  
<span data-ttu-id="92a1e-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="92a1e-105">\<runtime></span></span>  
<span data-ttu-id="92a1e-106">\<GCCpuGroup></span><span class="sxs-lookup"><span data-stu-id="92a1e-106">\<GCCpuGroup></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92a1e-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="92a1e-107">Syntax</span></span>  
  
```xml  
<GCCpuGroup    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92a1e-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="92a1e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="92a1e-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="92a1e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92a1e-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="92a1e-110">Attributes</span></span>  
  
|<span data-ttu-id="92a1e-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="92a1e-111">Attribute</span></span>|<span data-ttu-id="92a1e-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="92a1e-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="92a1e-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="92a1e-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="92a1e-114">Especifica se a coleta de lixo oferece suporte a vários grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="92a1e-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="92a1e-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="92a1e-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="92a1e-116">Valor</span><span class="sxs-lookup"><span data-stu-id="92a1e-116">Value</span></span>|<span data-ttu-id="92a1e-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="92a1e-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="92a1e-118">Coleta de lixo não oferece suporte a vários grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="92a1e-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="92a1e-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="92a1e-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="92a1e-120">Coleta de lixo dá suporte a vários grupos de CPU, se a coleta de lixo do servidor estiver habilitada.</span><span class="sxs-lookup"><span data-stu-id="92a1e-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="92a1e-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="92a1e-121">Child Elements</span></span>  
 <span data-ttu-id="92a1e-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="92a1e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="92a1e-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="92a1e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="92a1e-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="92a1e-124">Element</span></span>|<span data-ttu-id="92a1e-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="92a1e-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="92a1e-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="92a1e-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="92a1e-127">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="92a1e-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92a1e-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="92a1e-128">Remarks</span></span>  
 <span data-ttu-id="92a1e-129">Quando um computador tiver vários grupos de CPU e coleta de lixo do servidor está habilitada (consulte a [ \<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) elemento), permitindo que esse elemento se estende a coleta de lixo em todos os grupos de CPU e usa todos os núcleos em conta durante a criação e heaps de balanceamento.</span><span class="sxs-lookup"><span data-stu-id="92a1e-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="92a1e-130">Esse elemento só se aplica a threads de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="92a1e-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="92a1e-131">Para habilitar o tempo de execução distribui threads de usuário em todos os grupos de CPU, você deve habilitar também a [< Thread_UseAllCpuGroups >](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="92a1e-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92a1e-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="92a1e-132">Example</span></span>  
 <span data-ttu-id="92a1e-133">O exemplo a seguir mostra como habilitar a coleta de lixo para vários grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="92a1e-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="92a1e-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92a1e-134">See also</span></span>

- [<span data-ttu-id="92a1e-135">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="92a1e-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="92a1e-136">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="92a1e-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="92a1e-137">Para desabilitar a coleta de lixo simultânea</span><span class="sxs-lookup"><span data-stu-id="92a1e-137">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="92a1e-138">Coleta de lixo de estação de trabalho ou de servidor</span><span class="sxs-lookup"><span data-stu-id="92a1e-138">Workstation and server garbage collection</span></span>](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
