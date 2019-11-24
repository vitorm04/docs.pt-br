---
title: Elemento <GCCpuGroup>
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: ae9c96c9d49cf3f6be94da3f77b91423cab12e0b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430488"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="3e3c7-102">\<GCCpuGroup> Element</span><span class="sxs-lookup"><span data-stu-id="3e3c7-102">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="3e3c7-103">Especifica se a coleta de lixo oferece suporte a vários grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>

<span data-ttu-id="3e3c7-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3e3c7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3e3c7-105">&nbsp;&nbsp;[ **\<runtime>** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="3e3c7-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="3e3c7-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<GCCpuGroup>**</span><span class="sxs-lookup"><span data-stu-id="3e3c7-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="3e3c7-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e3c7-107">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3e3c7-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3e3c7-108">Attributes and Elements</span></span>

<span data-ttu-id="3e3c7-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="3e3c7-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="3e3c7-110">Attributes</span></span>

|<span data-ttu-id="3e3c7-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="3e3c7-111">Attribute</span></span>|<span data-ttu-id="3e3c7-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e3c7-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="3e3c7-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="3e3c7-114">Especifica se a coleta de lixo oferece suporte a vários grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="3e3c7-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="3e3c7-115">enabled Attribute</span></span>

|<span data-ttu-id="3e3c7-116">Valor</span><span class="sxs-lookup"><span data-stu-id="3e3c7-116">Value</span></span>|<span data-ttu-id="3e3c7-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e3c7-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="3e3c7-118">Garbage collection does not support multiple CPU groups.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="3e3c7-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="3e3c7-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="3e3c7-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3e3c7-121">Child Elements</span></span>

<span data-ttu-id="3e3c7-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3e3c7-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3e3c7-123">Parent Elements</span></span>

|<span data-ttu-id="3e3c7-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="3e3c7-124">Element</span></span>|<span data-ttu-id="3e3c7-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e3c7-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="3e3c7-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="3e3c7-127">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3e3c7-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="3e3c7-128">Remarks</span></span>

<span data-ttu-id="3e3c7-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="3e3c7-130">This element applies only to garbage collection threads.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="3e3c7-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="3e3c7-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3e3c7-132">Example</span></span>

<span data-ttu-id="3e3c7-133">The following example shows how to enable garbage collection for multiple CPU groups.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="3e3c7-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e3c7-134">See also</span></span>

- [<span data-ttu-id="3e3c7-135">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="3e3c7-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3e3c7-136">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="3e3c7-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="3e3c7-137">To disable concurrent garbage collection</span><span class="sxs-lookup"><span data-stu-id="3e3c7-137">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="3e3c7-138">Coleta de lixo de estação de trabalho ou de servidor</span><span class="sxs-lookup"><span data-stu-id="3e3c7-138">Workstation and server garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection)
