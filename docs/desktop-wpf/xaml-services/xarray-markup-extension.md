---
title: Extensão de marcação x:Array
ms.date: 03/30/2017
f1_keywords:
- x:Array
- xArray
helpviewer_keywords:
- x:Array [XAML Services]
- XAML [XAML Services], x:Array markup extension
ms.assetid: c5358e14-d24c-44c7-b5eb-6062a4fd981c
ms.openlocfilehash: b812939cbaa74576361de534c0d39ba45536cbcf
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555166"
---
# <a name="xarray-markup-extension"></a><span data-ttu-id="3a94b-102">Extensão de marcação x:Array</span><span class="sxs-lookup"><span data-stu-id="3a94b-102">x:Array Markup Extension</span></span>

<span data-ttu-id="3a94b-103">Fornece suporte geral para matrizes de objetos em XAML por meio de uma extensão de marcação.</span><span class="sxs-lookup"><span data-stu-id="3a94b-103">Provides general support for arrays of objects in XAML through a markup extension.</span></span> <span data-ttu-id="3a94b-104">Isso corresponde ao `x:ArrayExtension` tipo XAML em [MS-XAML].</span><span class="sxs-lookup"><span data-stu-id="3a94b-104">This corresponds to the `x:ArrayExtension` XAML type in [MS-XAML].</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="3a94b-105">Uso de elemento Object do XAML</span><span class="sxs-lookup"><span data-stu-id="3a94b-105">XAML Object Element Usage</span></span>

```xaml
<x:Array Type="typeName">
  arrayContents
</x:Array>
```

## <a name="xaml-values"></a><span data-ttu-id="3a94b-106">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="3a94b-106">XAML Values</span></span>

|||
|-|-|
|`typeName`|<span data-ttu-id="3a94b-107">O nome do tipo que seu `x:Array` conterá.</span><span class="sxs-lookup"><span data-stu-id="3a94b-107">The name of the type that your `x:Array` will contain.</span></span> <span data-ttu-id="3a94b-108">`typeName` pode ser (e geralmente é) prefixado para um namespace XAML que contém as definições de tipo XAML.</span><span class="sxs-lookup"><span data-stu-id="3a94b-108">`typeName` may be (and often is) prefixed for a XAML namespace that contains the XAML type definitions.</span></span>|
|`arrayContents`|<span data-ttu-id="3a94b-109">O conteúdo dos itens que é atribuído à `ArrayExtension.Items` propriedade intrínseca.</span><span class="sxs-lookup"><span data-stu-id="3a94b-109">The items content that is assigned to the intrinsic `ArrayExtension.Items` property.</span></span> <span data-ttu-id="3a94b-110">Normalmente, esses itens são especificados como um ou mais elementos de objeto contidos nas `x:Array` marcas de abertura e fechamento.</span><span class="sxs-lookup"><span data-stu-id="3a94b-110">Typically, these items are specified as one or more object elements contained within the `x:Array` opening and closing tags.</span></span> <span data-ttu-id="3a94b-111">Os objetos especificados aqui devem ser atribuíveis ao tipo XAML especificado em `typeName` .</span><span class="sxs-lookup"><span data-stu-id="3a94b-111">Objects specified here are expected to be assignable to the XAML type specified in `typeName`.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3a94b-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="3a94b-112">Remarks</span></span>

<span data-ttu-id="3a94b-113">`Type` é um atributo necessário para todos os `x:Array` elementos de objeto.</span><span class="sxs-lookup"><span data-stu-id="3a94b-113">`Type` is a required attribute for all `x:Array` object elements.</span></span> <span data-ttu-id="3a94b-114">Um `Type` valor de parâmetro não precisa usar uma `x:Type` extensão de marcação; o nome curto do tipo é um tipo XAML, que pode ser especificado como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3a94b-114">A `Type` parameter value does not need to use an `x:Type` markup extension; the short name of the type is   a XAML type, which can be specified as a string.</span></span>

<span data-ttu-id="3a94b-115">Na implementação de serviços XAML .NET, a relação entre o tipo XAML de entrada e o CLR <xref:System.Type> de saída da matriz criada é influenciada pelo contexto de serviço para extensões de marcação.</span><span class="sxs-lookup"><span data-stu-id="3a94b-115">In .NET XAML Services implementation, the relationship between the input XAML type and the output CLR <xref:System.Type> of the created array is influenced by service context for markup extensions.</span></span> <span data-ttu-id="3a94b-116">A saída <xref:System.Type> é o <xref:System.Xaml.XamlType.UnderlyingType%2A> do tipo XAML de entrada, depois de Pesquisar o necessário <xref:System.Xaml.XamlType> com base no contexto do esquema XAML e no <xref:System.Windows.Markup.IXamlTypeResolver> serviço que o contexto fornece.</span><span class="sxs-lookup"><span data-stu-id="3a94b-116">The output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input XAML type, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>

<span data-ttu-id="3a94b-117">Quando processado, o conteúdo da matriz é atribuído à `ArrayExtension.Items` propriedade intrínseca.</span><span class="sxs-lookup"><span data-stu-id="3a94b-117">When processed, the array contents are assigned to the `ArrayExtension.Items` intrinsic property.</span></span> <span data-ttu-id="3a94b-118">Na <xref:System.Windows.Markup.ArrayExtension> implementação, isso é representado por <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3a94b-118">In the <xref:System.Windows.Markup.ArrayExtension> implementation, this is represented by <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="3a94b-119">Na implementação de serviços XAML .NET, o tratamento para essa extensão de marcação é definido pela <xref:System.Windows.Markup.ArrayExtension> classe.</span><span class="sxs-lookup"><span data-stu-id="3a94b-119">In .NET XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.ArrayExtension> class.</span></span> <span data-ttu-id="3a94b-120"><xref:System.Windows.Markup.ArrayExtension> Não é lacrado e pode ser usado como base para uma implementação de extensão de marcação para um tipo de matriz personalizado.</span><span class="sxs-lookup"><span data-stu-id="3a94b-120"><xref:System.Windows.Markup.ArrayExtension> is not sealed, and could be used as the basis for a markup extension implementation for a custom array type.</span></span>

<span data-ttu-id="3a94b-121">`x:Array` é mais destinado à extensibilidade de idioma geral em XAML.</span><span class="sxs-lookup"><span data-stu-id="3a94b-121">`x:Array` is more intended for general language extensibility in XAML.</span></span> <span data-ttu-id="3a94b-122">Mas `x:Array` também pode ser útil para especificar valores XAML de determinadas propriedades que usam coleções com suporte a XAML como seu conteúdo de propriedade estruturada.</span><span class="sxs-lookup"><span data-stu-id="3a94b-122">But `x:Array` can also be useful for specifying XAML values of certain properties that take XAML-supported collections as their structured property content.</span></span> <span data-ttu-id="3a94b-123">Por exemplo, você pode especificar o conteúdo de uma <xref:System.Collections.IEnumerable> propriedade com um `x:Array` uso.</span><span class="sxs-lookup"><span data-stu-id="3a94b-123">For example, you could specify the contents of an <xref:System.Collections.IEnumerable> property with an `x:Array` usage.</span></span>

<span data-ttu-id="3a94b-124">`x:Array` é uma extensão da marcação.</span><span class="sxs-lookup"><span data-stu-id="3a94b-124">`x:Array` is a markup extension.</span></span> <span data-ttu-id="3a94b-125">Extensões de marcação são tipicamente implementadas quando existe um requisito que permite que valores de atributo sejam diferentes de valores literais ou nomes de manipuladores, e o requisito é mais global do que simplesmente colocar conversores de tipo em certos tipos ou propriedades.</span><span class="sxs-lookup"><span data-stu-id="3a94b-125">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="3a94b-126">`x:Array` é parcialmente uma exceção a essa regra porque, em vez de fornecer tratamento alternativo de valor de atributo, `x:Array` o fornece tratamento alternativo de seu conteúdo de texto interno.</span><span class="sxs-lookup"><span data-stu-id="3a94b-126">`x:Array` is partially an exception to that rule because instead of providing alternative attribute value handling, `x:Array` provides alternative handling of its inner text content.</span></span> <span data-ttu-id="3a94b-127">Esse comportamento permite que os tipos que não tenham suporte de um modelo de conteúdo existente sejam agrupados em uma matriz e referenciados posteriormente no code-behind acessando a matriz nomeada; Você pode chamar <xref:System.Array> métodos para obter itens de matriz individuais.</span><span class="sxs-lookup"><span data-stu-id="3a94b-127">This behavior enables types that might not be supported by an existing content model to be grouped into an array and referenced later in code-behind by accessing the named array; you can call <xref:System.Array> methods to get individual array items.</span></span>

<span data-ttu-id="3a94b-128">Todas as extensões de marcação em XAML usam as chaves ( {,} `)` em sua sintaxe de atributo, que é a Convenção pela qual um processador XAML reconhece que uma extensão de marcação deve processar o valor do atributo.</span><span class="sxs-lookup"><span data-stu-id="3a94b-128">All markup extensions in XAML use the braces ({,}`)` in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute value.</span></span> <span data-ttu-id="3a94b-129">Para obter mais informações sobre extensões de marcação em geral, consulte [conversores de tipos e extensões de marcação para XAML](type-converters-and-markup-extensions.md).</span><span class="sxs-lookup"><span data-stu-id="3a94b-129">For more information about markup extensions in general, see [Type Converters and Markup Extensions for XAML](type-converters-and-markup-extensions.md).</span></span>

<span data-ttu-id="3a94b-130">No XAML 2009, `x:Array` é definido como um primitivo de linguagem em vez de uma extensão de marcação.</span><span class="sxs-lookup"><span data-stu-id="3a94b-130">In XAML 2009, `x:Array` is defined as a language primitive instead of a markup extension.</span></span> <span data-ttu-id="3a94b-131">Para obter mais informações, consulte [tipos internos para primitivos comuns de linguagem XAML](types-for-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="3a94b-131">For more information, see [Built-in Types for Common XAML Language Primitives](types-for-primitives.md).</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="3a94b-132">Notas de uso do WPF</span><span class="sxs-lookup"><span data-stu-id="3a94b-132">WPF Usage Notes</span></span>

<span data-ttu-id="3a94b-133">Normalmente, os elementos de objeto que populam um `x:Array` não são elementos que existem no [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] namespace XAML e exigem um mapeamento de prefixo para um namespace XAML não padrão.</span><span class="sxs-lookup"><span data-stu-id="3a94b-133">Typically, the object elements that populate an `x:Array` are not elements that exist in the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML namespace, and require a prefix mapping to a non-default XAML namespace.</span></span>

<span data-ttu-id="3a94b-134">Por exemplo, a seguir está uma matriz simples de duas cadeias de caracteres, com o `sys` prefixo (e também `x` ) definido no nível da matriz.</span><span class="sxs-lookup"><span data-stu-id="3a94b-134">For example, the following is a simple array of two strings, with the `sys` prefix (and also `x`) defined at the level of the array.</span></span>

```xaml
<x:Array Type="sys:String"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <sys:String>Hello</sys:String>
  <sys:String>World</sys:String>
</x:Array>
```

<span data-ttu-id="3a94b-135">Para tipos personalizados que são usados como elementos de matriz, a classe também deve dar suporte aos requisitos para ser instanciada em XAML como elementos de objeto.</span><span class="sxs-lookup"><span data-stu-id="3a94b-135">For custom types that are used as array elements, the class must also support the requirements for being instantiated in XAML as object elements.</span></span> <span data-ttu-id="3a94b-136">Para obter mais informações, consulte [XAML e classes personalizadas para WPF](/dotnet/desktop/wpf/advanced/xaml-and-custom-classes-for-wpf).</span><span class="sxs-lookup"><span data-stu-id="3a94b-136">For more information, see [XAML and Custom Classes for WPF](/dotnet/desktop/wpf/advanced/xaml-and-custom-classes-for-wpf).</span></span>

## <a name="see-also"></a><span data-ttu-id="3a94b-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="3a94b-137">See also</span></span>

- [<span data-ttu-id="3a94b-138">Extensões de marcação e XAML WPF</span><span class="sxs-lookup"><span data-stu-id="3a94b-138">Markup Extensions and WPF XAML</span></span>](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)
- [<span data-ttu-id="3a94b-139">Tipos migrados do WPF para System.Xaml</span><span class="sxs-lookup"><span data-stu-id="3a94b-139">Types Migrated from WPF to System.Xaml</span></span>](/dotnet/desktop/wpf/advanced/types-migrated-from-wpf-to-system)
