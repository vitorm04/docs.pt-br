---
title: Elemento <NetFx45_CultureAwareComparerGetHashCode_LongStrings>
ms.date: 03/30/2017
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
ms.openlocfilehash: 193f9a15768e4060d977063117c07558bbb1d766
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116137"
---
# <a name="netfx45_cultureawarecomparergethashcode_longstrings-element"></a><span data-ttu-id="6ea8b-102">\<elemento de > NetFx45_CultureAwareComparerGetHashCode_LongStrings</span><span class="sxs-lookup"><span data-stu-id="6ea8b-102">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> Element</span></span>

<span data-ttu-id="6ea8b-103">Especifica se o tempo de execução usa uma quantidade fixa de memória para calcular códigos hash para o método <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6ea8b-103">Specifies whether the runtime uses a fixed amount of memory to calculate hash codes for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="6ea8b-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6ea8b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6ea8b-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="6ea8b-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="6ea8b-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<NetFx45_CultureAwareComparerGetHashCode_LongStrings >**</span><span class="sxs-lookup"><span data-stu-id="6ea8b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="6ea8b-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6ea8b-107">Syntax</span></span>

```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6ea8b-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6ea8b-108">Attributes and Elements</span></span>

<span data-ttu-id="6ea8b-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6ea8b-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="6ea8b-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="6ea8b-110">Attributes</span></span>

|<span data-ttu-id="6ea8b-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="6ea8b-111">Attribute</span></span>|<span data-ttu-id="6ea8b-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="6ea8b-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="6ea8b-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="6ea8b-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="6ea8b-114">Especifica se o Common Language Runtime atribui uma quantidade fixa de memória ao calcular códigos hash.</span><span class="sxs-lookup"><span data-stu-id="6ea8b-114">Specifies whether the common language runtime allocates a fixed amount of memory when calculating hash codes.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="6ea8b-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="6ea8b-115">enabled Attribute</span></span>

|<span data-ttu-id="6ea8b-116">Valor</span><span class="sxs-lookup"><span data-stu-id="6ea8b-116">Value</span></span>|<span data-ttu-id="6ea8b-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="6ea8b-117">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="6ea8b-118">0</span><span class="sxs-lookup"><span data-stu-id="6ea8b-118">0</span></span>|<span data-ttu-id="6ea8b-119">O Common Language Runtime aloca uma quantidade variável de memória para o método <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> para calcular códigos hash.</span><span class="sxs-lookup"><span data-stu-id="6ea8b-119">The common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span> <span data-ttu-id="6ea8b-120">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="6ea8b-120">This is the default.</span></span>|
|<span data-ttu-id="6ea8b-121">1</span><span class="sxs-lookup"><span data-stu-id="6ea8b-121">1</span></span>|<span data-ttu-id="6ea8b-122">O Common Language Runtime aloca uma quantidade fixa de memória para o método <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> para calcular códigos hash.</span><span class="sxs-lookup"><span data-stu-id="6ea8b-122">The common language runtime allocates a fixed amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="6ea8b-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6ea8b-123">Child Elements</span></span>

<span data-ttu-id="6ea8b-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6ea8b-124">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6ea8b-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6ea8b-125">Parent Elements</span></span>

|<span data-ttu-id="6ea8b-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="6ea8b-126">Element</span></span>|<span data-ttu-id="6ea8b-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="6ea8b-127">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="6ea8b-128">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6ea8b-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="6ea8b-129">Contém informações sobre opções de inicialização do runtime.</span><span class="sxs-lookup"><span data-stu-id="6ea8b-129">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6ea8b-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="6ea8b-130">Remarks</span></span>

<span data-ttu-id="6ea8b-131">Por padrão, o Common Language Runtime aloca uma quantidade variável de memória para o método <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> e um <xref:System.ArgumentException> pode ser disparado quando o método tentar calcular o código hash de cadeias de caracteres muito grandes (com comprimentos superiores a vários milhões de caracteres).</span><span class="sxs-lookup"><span data-stu-id="6ea8b-131">By default, the common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method, and an <xref:System.ArgumentException> can be thrown when the method attempts to compute the hash code of very large strings (over several million characters long).</span></span> <span data-ttu-id="6ea8b-132">Ao adicionar esse elemento a um arquivo de configuração do aplicativo e definir seu atributo `enabled` como "1", você poderá especificar que o método <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> use um algoritmo alternativo que aloque uma quantidade fixa de memória para o cálculo de códigos hash.</span><span class="sxs-lookup"><span data-stu-id="6ea8b-132">By adding this element to an application configuration file and setting its `enabled` attribute to "1", you can specify that the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method use an alternate algorithm that allocates a fixed amount of memory for the computation of hash codes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6ea8b-133">O elemento `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` não é usado em [!INCLUDE[win8](../../../../../includes/win8-md.md)] e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="6ea8b-133">The `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` element is not used in [!INCLUDE[win8](../../../../../includes/win8-md.md)] and later versions.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ea8b-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ea8b-134">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="6ea8b-135">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="6ea8b-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6ea8b-136">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="6ea8b-136">Configuration File Schema</span></span>](../index.md)
