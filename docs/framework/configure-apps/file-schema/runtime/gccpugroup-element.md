---
title: Elemento <GCCpuGroup>
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: 352890519c1a227d664d877c3123866e5e4e1657
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116839"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="25c70-102">\<elemento de > GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="25c70-102">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="25c70-103">Especifica se a coleta de lixo oferece suporte a vários grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="25c70-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>

<span data-ttu-id="25c70-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="25c70-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="25c70-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="25c70-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="25c70-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<GCCpuGroup >**</span><span class="sxs-lookup"><span data-stu-id="25c70-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="25c70-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="25c70-107">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="25c70-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="25c70-108">Attributes and Elements</span></span>

<span data-ttu-id="25c70-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="25c70-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="25c70-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="25c70-110">Attributes</span></span>

|<span data-ttu-id="25c70-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="25c70-111">Attribute</span></span>|<span data-ttu-id="25c70-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="25c70-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="25c70-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="25c70-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="25c70-114">Especifica se a coleta de lixo oferece suporte a vários grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="25c70-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="25c70-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="25c70-115">enabled Attribute</span></span>

|<span data-ttu-id="25c70-116">Valor</span><span class="sxs-lookup"><span data-stu-id="25c70-116">Value</span></span>|<span data-ttu-id="25c70-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="25c70-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="25c70-118">A coleta de lixo não dá suporte a vários grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="25c70-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="25c70-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="25c70-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="25c70-120">A coleta de lixo oferece suporte a vários grupos de CPU, se a coleta de lixo do servidor estiver habilitada.</span><span class="sxs-lookup"><span data-stu-id="25c70-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="25c70-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="25c70-121">Child Elements</span></span>

<span data-ttu-id="25c70-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="25c70-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="25c70-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="25c70-123">Parent Elements</span></span>

|<span data-ttu-id="25c70-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="25c70-124">Element</span></span>|<span data-ttu-id="25c70-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="25c70-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="25c70-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="25c70-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="25c70-127">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="25c70-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="25c70-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="25c70-128">Remarks</span></span>

<span data-ttu-id="25c70-129">Quando um computador tem vários grupos de CPU e a coleta de lixo do servidor está habilitada (consulte o elemento [\<gcServer >](gcserver-element.md) ), a habilitação desse elemento estende a coleta de lixo em todos os grupos de CPU e leva todos os núcleos em conta ao criar e balanceamento de heaps.</span><span class="sxs-lookup"><span data-stu-id="25c70-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="25c70-130">Este elemento aplica-se somente a threads de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="25c70-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="25c70-131">Para habilitar o tempo de execução para distribuir threads de usuário em todos os grupos de CPU, você também deve habilitar o elemento [\<Thread_UseAllCpuGroups >](thread-useallcpugroups-element.md) .</span><span class="sxs-lookup"><span data-stu-id="25c70-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="25c70-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="25c70-132">Example</span></span>

<span data-ttu-id="25c70-133">O exemplo a seguir mostra como habilitar a coleta de lixo para vários grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="25c70-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="25c70-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25c70-134">See also</span></span>

- [<span data-ttu-id="25c70-135">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="25c70-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="25c70-136">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="25c70-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="25c70-137">Para desabilitar a coleta de lixo simultânea</span><span class="sxs-lookup"><span data-stu-id="25c70-137">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="25c70-138">Coleta de lixo de estação de trabalho ou de servidor</span><span class="sxs-lookup"><span data-stu-id="25c70-138">Workstation and server garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
