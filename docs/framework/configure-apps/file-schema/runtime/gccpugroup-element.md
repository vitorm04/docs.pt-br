---
title: Elemento <GCCpuGroup>
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: f1cbe5a7109d6e4aae2e92710920a1c6b3a40d00
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "82102886"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="d9c98-102">Elemento \<GCCpuGroup></span><span class="sxs-lookup"><span data-stu-id="d9c98-102">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="d9c98-103">Especifica se a coleta de lixo oferece suporte a vários grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="d9c98-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**

## <a name="syntax"></a><span data-ttu-id="d9c98-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d9c98-104">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d9c98-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d9c98-105">Attributes and Elements</span></span>

<span data-ttu-id="d9c98-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d9c98-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d9c98-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="d9c98-107">Attributes</span></span>

|<span data-ttu-id="d9c98-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="d9c98-108">Attribute</span></span>|<span data-ttu-id="d9c98-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9c98-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="d9c98-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="d9c98-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="d9c98-111">Especifica se a coleta de lixo oferece suporte a vários grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="d9c98-111">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="d9c98-112">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="d9c98-112">enabled Attribute</span></span>

|<span data-ttu-id="d9c98-113">Valor</span><span class="sxs-lookup"><span data-stu-id="d9c98-113">Value</span></span>|<span data-ttu-id="d9c98-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9c98-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="d9c98-115">A coleta de lixo não dá suporte a vários grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="d9c98-115">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="d9c98-116">Este é o padrão.</span><span class="sxs-lookup"><span data-stu-id="d9c98-116">This is the default.</span></span>|
|`true`|<span data-ttu-id="d9c98-117">A coleta de lixo oferece suporte a vários grupos de CPU, se a coleta de lixo do servidor estiver habilitada.</span><span class="sxs-lookup"><span data-stu-id="d9c98-117">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="d9c98-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d9c98-118">Child Elements</span></span>

<span data-ttu-id="d9c98-119">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d9c98-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d9c98-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d9c98-120">Parent Elements</span></span>

|<span data-ttu-id="d9c98-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="d9c98-121">Element</span></span>|<span data-ttu-id="d9c98-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9c98-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="d9c98-123">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d9c98-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="d9c98-124">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="d9c98-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d9c98-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="d9c98-125">Remarks</span></span>

<span data-ttu-id="d9c98-126">Quando um computador tem vários grupos de CPU e a coleta de lixo do servidor está habilitada (Veja o [\<gcServer>](gcserver-element.md) elemento), habilitar esse elemento estende a coleta de lixo em todos os grupos de CPU e leva todos os núcleos em conta ao criar e balancear heaps.</span><span class="sxs-lookup"><span data-stu-id="d9c98-126">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="d9c98-127">Este elemento aplica-se somente a threads de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="d9c98-127">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="d9c98-128">Para habilitar o tempo de execução para distribuir threads de usuário em todos os grupos de CPU, você também deve habilitar o [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="d9c98-128">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="d9c98-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d9c98-129">Example</span></span>

<span data-ttu-id="d9c98-130">O exemplo a seguir mostra como habilitar a coleta de lixo para vários grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="d9c98-130">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="d9c98-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="d9c98-131">See also</span></span>

- [<span data-ttu-id="d9c98-132">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="d9c98-132">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d9c98-133">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="d9c98-133">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d9c98-134">Desabilitar a coleta de lixo simultânea</span><span class="sxs-lookup"><span data-stu-id="d9c98-134">Disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="d9c98-135">Coleta de lixo de estação de trabalho ou de servidor</span><span class="sxs-lookup"><span data-stu-id="d9c98-135">Workstation and server garbage collection</span></span>](../../../../standard/garbage-collection/workstation-server-gc.md)
