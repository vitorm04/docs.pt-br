---
title: '&lt;GCCpuGroup&gt; elemento'
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21ab18cded2b9a16fe2520547287198d3cfe6b74
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43416768"
---
# <a name="ltgccpugroupgt-element"></a><span data-ttu-id="7b40f-102">&lt;GCCpuGroup&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="7b40f-102">&lt;GCCpuGroup&gt; Element</span></span>
<span data-ttu-id="7b40f-103">Especifica se a coleta de lixo oferece suporte a vários grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="7b40f-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>  
  
 <span data-ttu-id="7b40f-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="7b40f-104">\<configuration></span></span>  
<span data-ttu-id="7b40f-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="7b40f-105">\<runtime></span></span>  
<span data-ttu-id="7b40f-106">\<GCCpuGroup></span><span class="sxs-lookup"><span data-stu-id="7b40f-106">\<GCCpuGroup></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b40f-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7b40f-107">Syntax</span></span>  
  
```xml  
<GCCpuGroup    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b40f-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7b40f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7b40f-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7b40f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b40f-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="7b40f-110">Attributes</span></span>  
  
|<span data-ttu-id="7b40f-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="7b40f-111">Attribute</span></span>|<span data-ttu-id="7b40f-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="7b40f-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="7b40f-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="7b40f-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="7b40f-114">Especifica se a coleta de lixo oferece suporte a vários grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="7b40f-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="7b40f-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="7b40f-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="7b40f-116">Valor</span><span class="sxs-lookup"><span data-stu-id="7b40f-116">Value</span></span>|<span data-ttu-id="7b40f-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="7b40f-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="7b40f-118">Coleta de lixo não oferece suporte a vários grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="7b40f-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="7b40f-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="7b40f-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="7b40f-120">Coleta de lixo dá suporte a vários grupos de CPU, se a coleta de lixo do servidor estiver habilitada.</span><span class="sxs-lookup"><span data-stu-id="7b40f-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7b40f-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7b40f-121">Child Elements</span></span>  
 <span data-ttu-id="7b40f-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="7b40f-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7b40f-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7b40f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7b40f-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="7b40f-124">Element</span></span>|<span data-ttu-id="7b40f-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="7b40f-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7b40f-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7b40f-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="7b40f-127">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="7b40f-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b40f-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="7b40f-128">Remarks</span></span>  
 <span data-ttu-id="7b40f-129">Quando um computador tiver vários grupos de CPU e coleta de lixo do servidor está habilitada (consulte a [ \<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) elemento), permitindo que esse elemento se estende a coleta de lixo em todos os grupos de CPU e usa todos os núcleos em conta durante a criação e heaps de balanceamento.</span><span class="sxs-lookup"><span data-stu-id="7b40f-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7b40f-130">Esse elemento só se aplica a threads de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="7b40f-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="7b40f-131">Para habilitar o tempo de execução distribui threads de usuário em todos os grupos de CPU, você deve habilitar também a [< Thread_UseAllCpuGroups >](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="7b40f-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b40f-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7b40f-132">Example</span></span>  
 <span data-ttu-id="7b40f-133">O exemplo a seguir mostra como habilitar a coleta de lixo para vários grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="7b40f-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7b40f-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7b40f-134">See Also</span></span>  
 [<span data-ttu-id="7b40f-135">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="7b40f-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="7b40f-136">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="7b40f-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="7b40f-137">Como: desabilitar a coleta de lixo simultânea</span><span class="sxs-lookup"><span data-stu-id="7b40f-137">How to: Disable Concurrent Garbage Collection</span></span>](https://msdn.microsoft.com/library/ba2c6c67-5778-497c-9fac-5f793b5500c7)  
 [<span data-ttu-id="7b40f-138">Coleta de lixo de estação de trabalho ou de servidor</span><span class="sxs-lookup"><span data-stu-id="7b40f-138">Workstation and server garbage collection</span></span>](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
