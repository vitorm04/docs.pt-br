---
title: Elemento <Thread_UseAllCpuGroups>
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
ms.openlocfilehash: a3a612c0ffbcb211157b9623d298ce8ad7a13e94
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115406"
---
# <a name="thread_useallcpugroups-element"></a><span data-ttu-id="098b7-102">Elemento \<Thread_UseAllCpuGroups></span><span class="sxs-lookup"><span data-stu-id="098b7-102">\<Thread_UseAllCpuGroups> Element</span></span>

<span data-ttu-id="098b7-103">Especifica se o runtime distribui threads gerenciados entre todos os grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="098b7-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<Thread_UseAllCpuGroups>**  

## <a name="syntax"></a><span data-ttu-id="098b7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="098b7-104">Syntax</span></span>

```xml
<Thread_UseAllCpuGroups
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="098b7-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="098b7-105">Attributes and Elements</span></span>

<span data-ttu-id="098b7-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="098b7-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="098b7-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="098b7-107">Attributes</span></span>

|<span data-ttu-id="098b7-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="098b7-108">Attribute</span></span>|<span data-ttu-id="098b7-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="098b7-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="098b7-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="098b7-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="098b7-111">Especifica se o runtime distribui threads gerenciados entre todos os grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="098b7-111">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="098b7-112">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="098b7-112">enabled Attribute</span></span>

|<span data-ttu-id="098b7-113">Valor</span><span class="sxs-lookup"><span data-stu-id="098b7-113">Value</span></span>|<span data-ttu-id="098b7-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="098b7-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="098b7-115">O tempo de execução não distribui threads gerenciados entre vários grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="098b7-115">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="098b7-116">Este é o padrão.</span><span class="sxs-lookup"><span data-stu-id="098b7-116">This is the default.</span></span>|
|`true`|<span data-ttu-id="098b7-117">O tempo de execução distribui threads gerenciados entre vários grupos de CPU, se o computador tiver vários grupos de CPU e o [\<GCCpuGroup>](gccpugroup-element.md) elemento estiver habilitado.</span><span class="sxs-lookup"><span data-stu-id="098b7-117">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](gccpugroup-element.md) element is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="098b7-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="098b7-118">Child Elements</span></span>

<span data-ttu-id="098b7-119">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="098b7-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="098b7-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="098b7-120">Parent Elements</span></span>

|<span data-ttu-id="098b7-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="098b7-121">Element</span></span>|<span data-ttu-id="098b7-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="098b7-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="098b7-123">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="098b7-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="098b7-124">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="098b7-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="098b7-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="098b7-125">Remarks</span></span>

<span data-ttu-id="098b7-126">Quando um computador tem vários grupos de CPU, a habilitação desse elemento faz com que o tempo de execução distribua threads gerenciados em todos os grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="098b7-126">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="098b7-127">Para usar esse recurso, você também deve habilitar o [\<GCCpuGroup>](gccpugroup-element.md) elemento, que estende a coleta de lixo para todos os grupos de CPU e leva todos os núcleos em conta ao criar e balancear heaps.</span><span class="sxs-lookup"><span data-stu-id="098b7-127">To use this feature, you must also enable the [\<GCCpuGroup>](gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="098b7-128">Habilitar o [\<GCCpuGroup>](gccpugroup-element.md) elemento requer a habilitação do [\<gcServer>](gcserver-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="098b7-128">Enabling the [\<GCCpuGroup>](gccpugroup-element.md) element requires enabling the [\<gcServer>](gcserver-element.md) element.</span></span> <span data-ttu-id="098b7-129">Se esses elementos não estiverem habilitados, a habilitação do `<Thread_UseAllCpuGroups>` elemento não terá nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="098b7-129">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>

## <a name="example"></a><span data-ttu-id="098b7-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="098b7-130">Example</span></span>

<span data-ttu-id="098b7-131">O exemplo a seguir mostra como habilitar o suporte para vários grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="098b7-131">The following example shows how to enable support for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <Thread_UseAllCpuGroups enabled="true"/>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="098b7-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="098b7-132">See also</span></span>

- [<span data-ttu-id="098b7-133">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="098b7-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="098b7-134">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="098b7-134">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="098b7-135">\<GCCpuGroup>Elementos</span><span class="sxs-lookup"><span data-stu-id="098b7-135">\<GCCpuGroup> Element</span></span>](gccpugroup-element.md)
