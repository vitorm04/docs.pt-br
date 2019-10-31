---
title: Elemento <Thread_UseAllCpuGroups>
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
ms.openlocfilehash: a3a612c0ffbcb211157b9623d298ce8ad7a13e94
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115406"
---
# <a name="thread_useallcpugroups-element"></a><span data-ttu-id="888ed-102">\<elemento de > Thread_UseAllCpuGroups</span><span class="sxs-lookup"><span data-stu-id="888ed-102">\<Thread_UseAllCpuGroups> Element</span></span>

<span data-ttu-id="888ed-103">Especifica se o tempo de execução distribui threads gerenciados entre todos os grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="888ed-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>

<span data-ttu-id="888ed-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="888ed-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="888ed-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="888ed-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="888ed-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<Thread_UseAllCpuGroups >**</span><span class="sxs-lookup"><span data-stu-id="888ed-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Thread_UseAllCpuGroups>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="888ed-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="888ed-107">Syntax</span></span>

```xml
<Thread_UseAllCpuGroups
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="888ed-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="888ed-108">Attributes and Elements</span></span>

<span data-ttu-id="888ed-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="888ed-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="888ed-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="888ed-110">Attributes</span></span>

|<span data-ttu-id="888ed-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="888ed-111">Attribute</span></span>|<span data-ttu-id="888ed-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="888ed-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="888ed-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="888ed-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="888ed-114">Especifica se o tempo de execução distribui threads gerenciados entre todos os grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="888ed-114">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="888ed-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="888ed-115">enabled Attribute</span></span>

|<span data-ttu-id="888ed-116">Valor</span><span class="sxs-lookup"><span data-stu-id="888ed-116">Value</span></span>|<span data-ttu-id="888ed-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="888ed-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="888ed-118">O tempo de execução não distribui threads gerenciados entre vários grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="888ed-118">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="888ed-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="888ed-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="888ed-120">O tempo de execução distribui threads gerenciados entre vários grupos de CPU, se o computador tiver vários grupos de CPU e o elemento [\<GCCpuGroup >](gccpugroup-element.md) estiver habilitado.</span><span class="sxs-lookup"><span data-stu-id="888ed-120">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](gccpugroup-element.md) element is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="888ed-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="888ed-121">Child Elements</span></span>

<span data-ttu-id="888ed-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="888ed-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="888ed-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="888ed-123">Parent Elements</span></span>

|<span data-ttu-id="888ed-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="888ed-124">Element</span></span>|<span data-ttu-id="888ed-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="888ed-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="888ed-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="888ed-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="888ed-127">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="888ed-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="888ed-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="888ed-128">Remarks</span></span>

<span data-ttu-id="888ed-129">Quando um computador tem vários grupos de CPU, a habilitação desse elemento faz com que o tempo de execução distribua threads gerenciados em todos os grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="888ed-129">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="888ed-130">Para usar esse recurso, você também deve habilitar o elemento [\<GCCpuGroup >](gccpugroup-element.md) , que estende a coleta de lixo a todos os grupos de CPU e leva todos os núcleos em conta ao criar e balancear heaps.</span><span class="sxs-lookup"><span data-stu-id="888ed-130">To use this feature, you must also enable the [\<GCCpuGroup>](gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="888ed-131">Habilitar o elemento [\<GCCpuGroup >](gccpugroup-element.md) requer a habilitação do elemento [\<> gcServer](gcserver-element.md) .</span><span class="sxs-lookup"><span data-stu-id="888ed-131">Enabling the [\<GCCpuGroup>](gccpugroup-element.md) element requires enabling the [\<gcServer>](gcserver-element.md) element.</span></span> <span data-ttu-id="888ed-132">Se esses elementos não estiverem habilitados, a habilitação do elemento `<Thread_UseAllCpuGroups>` não terá nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="888ed-132">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>

## <a name="example"></a><span data-ttu-id="888ed-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="888ed-133">Example</span></span>

<span data-ttu-id="888ed-134">O exemplo a seguir mostra como habilitar o suporte para vários grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="888ed-134">The following example shows how to enable support for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <Thread_UseAllCpuGroups enabled="true"/>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="888ed-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="888ed-135">See also</span></span>

- [<span data-ttu-id="888ed-136">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="888ed-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="888ed-137">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="888ed-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="888ed-138">\<elemento de > GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="888ed-138">\<GCCpuGroup> Element</span></span>](gccpugroup-element.md)
