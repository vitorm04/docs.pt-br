---
title: Elemento <Thread_UseAllCpuGroups>
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9758e009e012c8af5f5f7bd19dcd21f34b8c7d96
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66689741"
---
# <a name="threaduseallcpugroups-element"></a><span data-ttu-id="cdf47-102">\<Thread_UseAllCpuGroups > elemento</span><span class="sxs-lookup"><span data-stu-id="cdf47-102">\<Thread_UseAllCpuGroups> Element</span></span>

<span data-ttu-id="cdf47-103">Especifica se o tempo de execução distribui threads gerenciados entre todos os grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="cdf47-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>

<span data-ttu-id="cdf47-104">\<configuration>\\</span><span class="sxs-lookup"><span data-stu-id="cdf47-104">\<configuration>\\</span></span>
<span data-ttu-id="cdf47-105">\<runtime>\\</span><span class="sxs-lookup"><span data-stu-id="cdf47-105">\<runtime>\\</span></span>
<span data-ttu-id="cdf47-106">\<Thread_UseAllCpuGroups></span><span class="sxs-lookup"><span data-stu-id="cdf47-106">\<Thread_UseAllCpuGroups></span></span>

## <a name="syntax"></a><span data-ttu-id="cdf47-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cdf47-107">Syntax</span></span>

```xml
<Thread_UseAllCpuGroups
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cdf47-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cdf47-108">Attributes and Elements</span></span>

<span data-ttu-id="cdf47-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cdf47-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="cdf47-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="cdf47-110">Attributes</span></span>

|<span data-ttu-id="cdf47-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="cdf47-111">Attribute</span></span>|<span data-ttu-id="cdf47-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="cdf47-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="cdf47-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="cdf47-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="cdf47-114">Especifica se o tempo de execução distribui threads gerenciados entre todos os grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="cdf47-114">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="cdf47-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="cdf47-115">enabled Attribute</span></span>

|<span data-ttu-id="cdf47-116">Valor</span><span class="sxs-lookup"><span data-stu-id="cdf47-116">Value</span></span>|<span data-ttu-id="cdf47-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="cdf47-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="cdf47-118">O tempo de execução não distribui threads gerenciados entre vários grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="cdf47-118">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="cdf47-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="cdf47-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="cdf47-120">O tempo de execução distribui threads gerenciados entre vários grupos de CPU, se o computador tiver vários grupos de CPU e o [ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) elemento está habilitado.</span><span class="sxs-lookup"><span data-stu-id="cdf47-120">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="cdf47-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cdf47-121">Child Elements</span></span>

<span data-ttu-id="cdf47-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="cdf47-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cdf47-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cdf47-123">Parent Elements</span></span>

|<span data-ttu-id="cdf47-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="cdf47-124">Element</span></span>|<span data-ttu-id="cdf47-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="cdf47-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="cdf47-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cdf47-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="cdf47-127">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="cdf47-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cdf47-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="cdf47-128">Remarks</span></span>

<span data-ttu-id="cdf47-129">Quando um computador tiver vários grupos de CPU, a ativação deste elemento faz com que o tempo de execução distribui threads gerenciados entre todos os grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="cdf47-129">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="cdf47-130">Para usar esse recurso, você deve habilitar também a [ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) elemento, que estende a coleta de lixo para todos os grupos de CPU e leva em conta durante a criação e heaps de balanceamento a todos os núcleos.</span><span class="sxs-lookup"><span data-stu-id="cdf47-130">To use this feature, you must also enable the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="cdf47-131">Habilitando a [ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) elemento requer a habilitação de [ \<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="cdf47-131">Enabling the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element requires enabling the [\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element.</span></span> <span data-ttu-id="cdf47-132">Se esses elementos não estiverem habilitados, habilitando o `<Thread_UseAllCpuGroups>` elemento não tem nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="cdf47-132">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>

## <a name="example"></a><span data-ttu-id="cdf47-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cdf47-133">Example</span></span>

<span data-ttu-id="cdf47-134">O exemplo a seguir mostra como habilitar o suporte para vários grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="cdf47-134">The following example shows how to enable support for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <Thread_UseAllCpuGroups enabled="true"/>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="cdf47-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cdf47-135">See also</span></span>

- [<span data-ttu-id="cdf47-136">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="cdf47-136">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="cdf47-137">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="cdf47-137">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="cdf47-138">\<GCCpuGroup > elemento</span><span class="sxs-lookup"><span data-stu-id="cdf47-138">\<GCCpuGroup> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)
