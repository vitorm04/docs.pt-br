---
title: Elemento <Thread_UseAllCpuGroups>
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e964f1b2861926803b0449be06cbfd9567ac74a3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252281"
---
# <a name="thread_useallcpugroups-element"></a><span data-ttu-id="8071b-102">\<Elemento de > Thread_UseAllCpuGroups</span><span class="sxs-lookup"><span data-stu-id="8071b-102">\<Thread_UseAllCpuGroups> Element</span></span>

<span data-ttu-id="8071b-103">Especifica se o tempo de execução distribui threads gerenciados entre todos os grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="8071b-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>

<span data-ttu-id="8071b-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8071b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8071b-105">&nbsp;&nbsp;[ **\<> de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="8071b-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="8071b-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<> Thread_UseAllCpuGroups**</span><span class="sxs-lookup"><span data-stu-id="8071b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Thread_UseAllCpuGroups>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="8071b-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8071b-107">Syntax</span></span>

```xml
<Thread_UseAllCpuGroups
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8071b-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8071b-108">Attributes and Elements</span></span>

<span data-ttu-id="8071b-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8071b-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8071b-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="8071b-110">Attributes</span></span>

|<span data-ttu-id="8071b-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="8071b-111">Attribute</span></span>|<span data-ttu-id="8071b-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="8071b-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="8071b-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="8071b-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="8071b-114">Especifica se o tempo de execução distribui threads gerenciados entre todos os grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="8071b-114">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="8071b-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="8071b-115">enabled Attribute</span></span>

|<span data-ttu-id="8071b-116">Valor</span><span class="sxs-lookup"><span data-stu-id="8071b-116">Value</span></span>|<span data-ttu-id="8071b-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="8071b-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="8071b-118">O tempo de execução não distribui threads gerenciados entre vários grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="8071b-118">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="8071b-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="8071b-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="8071b-120">O tempo de execução distribui threads gerenciados entre vários grupos de CPU, se o computador tiver vários grupos de CPU e o elemento de [ \<> GCCpuGroup](gccpugroup-element.md) estiver habilitado.</span><span class="sxs-lookup"><span data-stu-id="8071b-120">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](gccpugroup-element.md) element is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="8071b-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8071b-121">Child Elements</span></span>

<span data-ttu-id="8071b-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8071b-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8071b-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8071b-123">Parent Elements</span></span>

|<span data-ttu-id="8071b-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="8071b-124">Element</span></span>|<span data-ttu-id="8071b-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="8071b-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="8071b-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8071b-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="8071b-127">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="8071b-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8071b-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="8071b-128">Remarks</span></span>

<span data-ttu-id="8071b-129">Quando um computador tem vários grupos de CPU, a habilitação desse elemento faz com que o tempo de execução distribua threads gerenciados em todos os grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="8071b-129">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="8071b-130">Para usar esse recurso, você também deve habilitar o elemento de [ \<> GCCpuGroup](gccpugroup-element.md) , que estende a coleta de lixo para todos os grupos de CPU e leva todos os núcleos em conta ao criar e balancear heaps.</span><span class="sxs-lookup"><span data-stu-id="8071b-130">To use this feature, you must also enable the [\<GCCpuGroup>](gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="8071b-131">Habilitar o [ \<elemento > GCCpuGroup](gccpugroup-element.md) requer a habilitação do [ \<elemento gcServer >](gcserver-element.md) .</span><span class="sxs-lookup"><span data-stu-id="8071b-131">Enabling the [\<GCCpuGroup>](gccpugroup-element.md) element requires enabling the [\<gcServer>](gcserver-element.md) element.</span></span> <span data-ttu-id="8071b-132">Se esses elementos não estiverem habilitados, a `<Thread_UseAllCpuGroups>` habilitação do elemento não terá nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="8071b-132">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>

## <a name="example"></a><span data-ttu-id="8071b-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8071b-133">Example</span></span>

<span data-ttu-id="8071b-134">O exemplo a seguir mostra como habilitar o suporte para vários grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="8071b-134">The following example shows how to enable support for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <Thread_UseAllCpuGroups enabled="true"/>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="8071b-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8071b-135">See also</span></span>

- [<span data-ttu-id="8071b-136">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="8071b-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="8071b-137">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="8071b-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="8071b-138">\<Elemento de > GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="8071b-138">\<GCCpuGroup> Element</span></span>](gccpugroup-element.md)
