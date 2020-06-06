---
title: Elemento <NetFx45_CultureAwareComparerGetHashCode_LongStrings>
ms.date: 03/30/2017
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
ms.openlocfilehash: 413eb6c6e61b509135601c65cf045eabd849e8b3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74802118"
---
# <a name="netfx45_cultureawarecomparergethashcode_longstrings-element"></a><span data-ttu-id="270fa-102">Elemento \<NetFx45_CultureAwareComparerGetHashCode_LongStrings></span><span class="sxs-lookup"><span data-stu-id="270fa-102">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> Element</span></span>

<span data-ttu-id="270fa-103">Especifica se o runtime usa uma quantidade fixa de memória para calcular códigos hash para o método <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="270fa-103">Specifies whether the runtime uses a fixed amount of memory to calculate hash codes for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>**  

## <a name="syntax"></a><span data-ttu-id="270fa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="270fa-104">Syntax</span></span>

```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">
```

## <a name="attributes-and-elements"></a><span data-ttu-id="270fa-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="270fa-105">Attributes and Elements</span></span>

<span data-ttu-id="270fa-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="270fa-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="270fa-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="270fa-107">Attributes</span></span>

|<span data-ttu-id="270fa-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="270fa-108">Attribute</span></span>|<span data-ttu-id="270fa-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="270fa-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="270fa-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="270fa-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="270fa-111">Especifica se o Common Language Runtime atribui uma quantidade fixa de memória ao calcular códigos hash.</span><span class="sxs-lookup"><span data-stu-id="270fa-111">Specifies whether the common language runtime allocates a fixed amount of memory when calculating hash codes.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="270fa-112">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="270fa-112">enabled Attribute</span></span>

|<span data-ttu-id="270fa-113">Valor</span><span class="sxs-lookup"><span data-stu-id="270fa-113">Value</span></span>|<span data-ttu-id="270fa-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="270fa-114">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="270fa-115">0</span><span class="sxs-lookup"><span data-stu-id="270fa-115">0</span></span>|<span data-ttu-id="270fa-116">O Common Language Runtime aloca uma quantidade variável de memória para o método <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> para calcular códigos hash.</span><span class="sxs-lookup"><span data-stu-id="270fa-116">The common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span> <span data-ttu-id="270fa-117">Este é o padrão.</span><span class="sxs-lookup"><span data-stu-id="270fa-117">This is the default.</span></span>|
|<span data-ttu-id="270fa-118">1</span><span class="sxs-lookup"><span data-stu-id="270fa-118">1</span></span>|<span data-ttu-id="270fa-119">O Common Language Runtime aloca uma quantidade fixa de memória para o método <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> para calcular códigos hash.</span><span class="sxs-lookup"><span data-stu-id="270fa-119">The common language runtime allocates a fixed amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="270fa-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="270fa-120">Child Elements</span></span>

<span data-ttu-id="270fa-121">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="270fa-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="270fa-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="270fa-122">Parent Elements</span></span>

|<span data-ttu-id="270fa-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="270fa-123">Element</span></span>|<span data-ttu-id="270fa-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="270fa-124">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="270fa-125">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="270fa-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="270fa-126">Contém informações sobre opções de inicialização do runtime.</span><span class="sxs-lookup"><span data-stu-id="270fa-126">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="270fa-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="270fa-127">Remarks</span></span>

<span data-ttu-id="270fa-128">Por padrão, o Common Language Runtime aloca uma quantidade variável de memória para o método <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> e um <xref:System.ArgumentException> pode ser disparado quando o método tentar calcular o código hash de cadeias de caracteres muito grandes (com comprimentos superiores a vários milhões de caracteres).</span><span class="sxs-lookup"><span data-stu-id="270fa-128">By default, the common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method, and an <xref:System.ArgumentException> can be thrown when the method attempts to compute the hash code of very large strings (over several million characters long).</span></span> <span data-ttu-id="270fa-129">Ao adicionar esse elemento a um arquivo de configuração do aplicativo e definir seu atributo `enabled` como "1", você poderá especificar que o método <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> use um algoritmo alternativo que aloque uma quantidade fixa de memória para o cálculo de códigos hash.</span><span class="sxs-lookup"><span data-stu-id="270fa-129">By adding this element to an application configuration file and setting its `enabled` attribute to "1", you can specify that the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method use an alternate algorithm that allocates a fixed amount of memory for the computation of hash codes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="270fa-130">O `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` elemento não é usado no Windows 8 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="270fa-130">The `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` element is not used in Windows 8 and later versions.</span></span>

## <a name="see-also"></a><span data-ttu-id="270fa-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="270fa-131">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="270fa-132">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="270fa-132">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="270fa-133">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="270fa-133">Configuration File Schema</span></span>](../index.md)
