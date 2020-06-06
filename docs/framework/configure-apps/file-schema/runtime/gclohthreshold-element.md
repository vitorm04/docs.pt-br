---
title: Elemento GCLOHThreshold
ms.date: 11/20/2019
helpviewer_keywords:
- GCLOHThreshold element
- <GCLOHThreshold> element
ms.openlocfilehash: d72dc9d27984f60dfb6296217263ce8b176093c6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74451216"
---
# <a name="gclohthreshold-element"></a><span data-ttu-id="67b93-102">Elemento GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="67b93-102">GCLOHThreshold element</span></span>

<span data-ttu-id="67b93-103">Especifica o tamanho do limite, em bytes, que faz com que o coletor de lixo coloque objetos na LOH (Large Object heap).</span><span class="sxs-lookup"><span data-stu-id="67b93-103">Specifies the threshold size, in bytes, that causes the garbage collector to put objects on the large object heap (LOH).</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold>

## <a name="syntax"></a><span data-ttu-id="67b93-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="67b93-104">Syntax</span></span>

```xml
<GCLOHThreshold
   enabled="nnnn"/>
```

## <a name="attributes"></a><span data-ttu-id="67b93-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="67b93-105">Attributes</span></span>

|<span data-ttu-id="67b93-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="67b93-106">Attribute</span></span>|<span data-ttu-id="67b93-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="67b93-107">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="67b93-108">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="67b93-108">Required attribute.</span></span><br /><br /><span data-ttu-id="67b93-109">Especifica o tamanho do limite que faz com que os objetos vá para a heap de objeto grande.</span><span class="sxs-lookup"><span data-stu-id="67b93-109">Specifies the threshold size that causes objects to go on the large object heap.</span></span>|

### <a name="enabled-attribute"></a><span data-ttu-id="67b93-110">atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="67b93-110">enabled attribute</span></span>

|<span data-ttu-id="67b93-111">Valor</span><span class="sxs-lookup"><span data-stu-id="67b93-111">Value</span></span>|<span data-ttu-id="67b93-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="67b93-112">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="67b93-113">O tamanho do limite, em bytes, que faz com que os objetos vá para a heap de objeto grande.</span><span class="sxs-lookup"><span data-stu-id="67b93-113">The threshold size, in bytes, that causes objects to go on the large object heap.</span></span>|

## <a name="child-elements"></a><span data-ttu-id="67b93-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="67b93-114">Child elements</span></span>

<span data-ttu-id="67b93-115">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="67b93-115">None.</span></span>

## <a name="parent-elements"></a><span data-ttu-id="67b93-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="67b93-116">Parent elements</span></span>

|<span data-ttu-id="67b93-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="67b93-117">Element</span></span>|<span data-ttu-id="67b93-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="67b93-118">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="67b93-119">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="67b93-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="67b93-120">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="67b93-120">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="67b93-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="67b93-121">Remarks</span></span>

<span data-ttu-id="67b93-122">Essa configuração foi introduzida no .NET Framework 4,8.</span><span class="sxs-lookup"><span data-stu-id="67b93-122">This setting was introduced in .NET Framework 4.8.</span></span>

## <a name="see-also"></a><span data-ttu-id="67b93-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="67b93-123">See also</span></span>

- [<span data-ttu-id="67b93-124">Esquema de configurações de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="67b93-124">Run-time settings schema</span></span>](index.md)
- [<span data-ttu-id="67b93-125">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="67b93-125">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="67b93-126">Conceitos básicos da coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="67b93-126">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="67b93-127">Opções de configuração de tempo de execução do NET Core para GC</span><span class="sxs-lookup"><span data-stu-id="67b93-127">NET Core run-time config options for GC</span></span>](../../../../core/run-time-config/garbage-collector.md)
