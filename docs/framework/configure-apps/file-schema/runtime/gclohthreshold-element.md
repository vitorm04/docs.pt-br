---
title: GCLOHThreshold element
ms.date: 11/20/2019
helpviewer_keywords:
- GCLOHThreshold element
- <GCLOHThreshold> element
ms.openlocfilehash: d72dc9d27984f60dfb6296217263ce8b176093c6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451216"
---
# <a name="gclohthreshold-element"></a><span data-ttu-id="344cd-102">GCLOHThreshold element</span><span class="sxs-lookup"><span data-stu-id="344cd-102">GCLOHThreshold element</span></span>

<span data-ttu-id="344cd-103">Specifies the threshold size, in bytes, that causes the garbage collector to put objects on the large object heap (LOH).</span><span class="sxs-lookup"><span data-stu-id="344cd-103">Specifies the threshold size, in bytes, that causes the garbage collector to put objects on the large object heap (LOH).</span></span>

<span data-ttu-id="344cd-104">[\<configuration>](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="344cd-104">[\<configuration>](../configuration-element.md)</span></span>\
<span data-ttu-id="344cd-105">&nbsp;&nbsp;[\<runtime>](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="344cd-105">&nbsp;&nbsp;[\<runtime>](runtime-element.md)</span></span>\
<span data-ttu-id="344cd-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold></span><span class="sxs-lookup"><span data-stu-id="344cd-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold></span></span>

## <a name="syntax"></a><span data-ttu-id="344cd-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="344cd-107">Syntax</span></span>

```xml
<GCLOHThreshold
   enabled="nnnn"/>
```

## <a name="attributes"></a><span data-ttu-id="344cd-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="344cd-108">Attributes</span></span>

|<span data-ttu-id="344cd-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="344cd-109">Attribute</span></span>|<span data-ttu-id="344cd-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="344cd-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="344cd-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="344cd-111">Required attribute.</span></span><br /><br /><span data-ttu-id="344cd-112">Specifies the threshold size that causes objects to go on the large object heap.</span><span class="sxs-lookup"><span data-stu-id="344cd-112">Specifies the threshold size that causes objects to go on the large object heap.</span></span>|

### <a name="enabled-attribute"></a><span data-ttu-id="344cd-113">enabled attribute</span><span class="sxs-lookup"><span data-stu-id="344cd-113">enabled attribute</span></span>

|<span data-ttu-id="344cd-114">Valor</span><span class="sxs-lookup"><span data-stu-id="344cd-114">Value</span></span>|<span data-ttu-id="344cd-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="344cd-115">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="344cd-116">The threshold size, in bytes, that causes objects to go on the large object heap.</span><span class="sxs-lookup"><span data-stu-id="344cd-116">The threshold size, in bytes, that causes objects to go on the large object heap.</span></span>|

## <a name="child-elements"></a><span data-ttu-id="344cd-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="344cd-117">Child elements</span></span>

<span data-ttu-id="344cd-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="344cd-118">None.</span></span>

## <a name="parent-elements"></a><span data-ttu-id="344cd-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="344cd-119">Parent elements</span></span>

|<span data-ttu-id="344cd-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="344cd-120">Element</span></span>|<span data-ttu-id="344cd-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="344cd-121">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="344cd-122">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="344cd-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="344cd-123">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="344cd-123">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="344cd-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="344cd-124">Remarks</span></span>

<span data-ttu-id="344cd-125">This setting was introduced in .NET Framework 4.8.</span><span class="sxs-lookup"><span data-stu-id="344cd-125">This setting was introduced in .NET Framework 4.8.</span></span>

## <a name="see-also"></a><span data-ttu-id="344cd-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="344cd-126">See also</span></span>

- [<span data-ttu-id="344cd-127">Run-time settings schema</span><span class="sxs-lookup"><span data-stu-id="344cd-127">Run-time settings schema</span></span>](index.md)
- [<span data-ttu-id="344cd-128">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="344cd-128">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="344cd-129">Noções básicas da coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="344cd-129">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="344cd-130">NET Core run-time config options for GC</span><span class="sxs-lookup"><span data-stu-id="344cd-130">NET Core run-time config options for GC</span></span>](../../../../core/run-time-config/garbage-collector.md)
