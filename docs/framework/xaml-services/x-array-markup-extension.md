---
title: "Extensão de marcação x:Array"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- x:Array
- xArray
helpviewer_keywords:
- x:Array [XAML Services]
- XAML [XAML Services], x:Array markup extension
ms.assetid: c5358e14-d24c-44c7-b5eb-6062a4fd981c
caps.latest.revision: "20"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bc2304ba68956b705904c72e29a17bdac4536c79
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="xarray-markup-extension"></a><span data-ttu-id="4c8ad-102">Extensão de marcação x:Array</span><span class="sxs-lookup"><span data-stu-id="4c8ad-102">x:Array Markup Extension</span></span>
<span data-ttu-id="4c8ad-103">Fornece suporte geral para matrizes de objetos por meio de uma extensão de marcação XAML.</span><span class="sxs-lookup"><span data-stu-id="4c8ad-103">Provides general support for arrays of objects in XAML through a markup extension.</span></span> <span data-ttu-id="4c8ad-104">Isso corresponde do `x:ArrayExtension` tipo XAML em [MS-XAML].</span><span class="sxs-lookup"><span data-stu-id="4c8ad-104">This corresponds to the `x:ArrayExtension` XAML type in [MS-XAML].</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="4c8ad-105">Uso de elemento Object do XAML</span><span class="sxs-lookup"><span data-stu-id="4c8ad-105">XAML Object Element Usage</span></span>  
  
```  
<x:Array Type="typeName">  
  arrayContents  
</x:Array>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="4c8ad-106">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="4c8ad-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`typeName`|<span data-ttu-id="4c8ad-107">O nome do tipo que seu `x:Array` conterá.</span><span class="sxs-lookup"><span data-stu-id="4c8ad-107">The name of the type that your `x:Array` will contain.</span></span> <span data-ttu-id="4c8ad-108">`typeName`pode ser (e geralmente é) o prefixo para uma XAML definições de tipo de namespace que contém o XAML.</span><span class="sxs-lookup"><span data-stu-id="4c8ad-108">`typeName` may be (and often is) prefixed for a XAML namespace that contains the XAML type definitions.</span></span>|  
|`arrayContents`|<span data-ttu-id="4c8ad-109">O conteúdo de itens que é atribuído a intrínseca `ArrayExtension.Items` propriedade.</span><span class="sxs-lookup"><span data-stu-id="4c8ad-109">The items content that is assigned to the intrinsic `ArrayExtension.Items` property.</span></span> <span data-ttu-id="4c8ad-110">Normalmente, esses itens são especificados como um ou mais elementos de objeto dentro de `x:Array` marcas abertura e fechamento.</span><span class="sxs-lookup"><span data-stu-id="4c8ad-110">Typically, these items are specified as one or more object elements contained within the `x:Array` opening and closing tags.</span></span> <span data-ttu-id="4c8ad-111">Os objetos especificados aqui devem ser atribuível ao tipo de XAML especificado em `typeName`.</span><span class="sxs-lookup"><span data-stu-id="4c8ad-111">Objects specified here are expected to be assignable to the XAML type specified in `typeName`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c8ad-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="4c8ad-112">Remarks</span></span>  
 <span data-ttu-id="4c8ad-113">`Type`é um atributo necessário para todos os `x:Array` elementos de objeto.</span><span class="sxs-lookup"><span data-stu-id="4c8ad-113">`Type` is a required attribute for all `x:Array` object elements.</span></span> <span data-ttu-id="4c8ad-114">Um `Type` o valor do parâmetro não é necessário usar um `x:Type` extensão de marcação; curto nome do tipo é um tipo XAML, que pode ser especificado como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4c8ad-114">A `Type` parameter value does not need to use an `x:Type` markup extension; the short name of the type is   a XAML type, which can be specified as a string.</span></span>  
  
 <span data-ttu-id="4c8ad-115">A implementação de serviços XAML do .NET Framework, a relação entre o tipo de XAML de entrada e saída CLR <xref:System.Type> da matriz criada é influenciado pelo contexto de serviço para extensões de marcação.</span><span class="sxs-lookup"><span data-stu-id="4c8ad-115">In the .NET Framework XAML Services implementation, the relationship between the input XAML type and the output CLR <xref:System.Type> of the created array is influenced by service context for markup extensions.</span></span> <span data-ttu-id="4c8ad-116">A saída <xref:System.Type> é o <xref:System.Xaml.XamlType.UnderlyingType%2A> do tipo de entrada XAML, depois de pesquisar necessários <xref:System.Xaml.XamlType> com base no contexto do esquema XAML e o <xref:System.Windows.Markup.IXamlTypeResolver> fornece o contexto de serviço.</span><span class="sxs-lookup"><span data-stu-id="4c8ad-116">The output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input XAML type, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>  
  
 <span data-ttu-id="4c8ad-117">Quando processado, o conteúdo da matriz é atribuído para a `ArrayExtension.Items` propriedade intrínseca.</span><span class="sxs-lookup"><span data-stu-id="4c8ad-117">When processed, the array contents are assigned to the `ArrayExtension.Items` intrinsic property.</span></span> <span data-ttu-id="4c8ad-118">No <xref:System.Windows.Markup.ArrayExtension> implementação, isso é representado por <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4c8ad-118">In the <xref:System.Windows.Markup.ArrayExtension> implementation, this is represented by <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="4c8ad-119">Na implementação de serviços XAML do .NET Framework, o tratamento para esta extensão de marcação é definida pelo <xref:System.Windows.Markup.ArrayExtension> classe.</span><span class="sxs-lookup"><span data-stu-id="4c8ad-119">In the .NET Framework XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.ArrayExtension> class.</span></span> <span data-ttu-id="4c8ad-120"><xref:System.Windows.Markup.ArrayExtension>não for fechada e pode ser usado como base para uma implementação de extensão de marcação para um tipo personalizado de matriz.</span><span class="sxs-lookup"><span data-stu-id="4c8ad-120"><xref:System.Windows.Markup.ArrayExtension> is not sealed, and could be used as the basis for a markup extension implementation for a custom array type.</span></span>  
  
 <span data-ttu-id="4c8ad-121">`x:Array`é que mais destinado geral extensibilidade de idioma em XAML.</span><span class="sxs-lookup"><span data-stu-id="4c8ad-121">`x:Array` is more intended for general language extensibility in XAML.</span></span> <span data-ttu-id="4c8ad-122">Mas `x:Array` também pode ser útil para especificar os valores de determinadas propriedades que usam coleções de suporte para XAML como sua propriedade estruturada conteúdo XAML.</span><span class="sxs-lookup"><span data-stu-id="4c8ad-122">But `x:Array` can also be useful for specifying XAML values of certain properties that take XAML-supported collections as their structured property content.</span></span> <span data-ttu-id="4c8ad-123">Por exemplo, você pode especificar o conteúdo de um <xref:System.Collections.IEnumerable> propriedade com um `x:Array` uso.</span><span class="sxs-lookup"><span data-stu-id="4c8ad-123">For example, you could specify the contents of an <xref:System.Collections.IEnumerable> property with an `x:Array` usage.</span></span>  
  
 <span data-ttu-id="4c8ad-124">`x:Array` é uma extensão da marcação.</span><span class="sxs-lookup"><span data-stu-id="4c8ad-124">`x:Array` is a markup extension.</span></span> <span data-ttu-id="4c8ad-125">Extensões de marcação são tipicamente implementadas quando existe um requisito que permite que valores de atributo sejam diferentes de valores literais ou nomes de manipuladores, e o requisito é mais global do que simplesmente colocar conversores de tipo em certos tipos ou propriedades.</span><span class="sxs-lookup"><span data-stu-id="4c8ad-125">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="4c8ad-126">`x:Array`é uma exceção a essa regra parcialmente, porque em vez de fornecer o tratamento do valor de atributo alternativo, `x:Array` fornece tratamento alternativo de seu conteúdo de texto interno.</span><span class="sxs-lookup"><span data-stu-id="4c8ad-126">`x:Array` is partially an exception to that rule because instead of providing alternative attribute value handling, `x:Array` provides alternative handling of its inner text content.</span></span> <span data-ttu-id="4c8ad-127">Esse comportamento permite que os tipos que não podem ter suporte por um modelo de conteúdo existente para ser agrupadas em uma matriz e referenciados mais tarde no code-behind, acessando a matriz nomeada; Você pode chamar <xref:System.Array> métodos para obter itens individuais de matriz.</span><span class="sxs-lookup"><span data-stu-id="4c8ad-127">This behavior enables types that might not be supported by an existing content model to be grouped into an array and referenced later in code-behind by accessing the named array; you can call <xref:System.Array> methods to get individual array items.</span></span>  
  
 <span data-ttu-id="4c8ad-128">Todas as extensões de marcação XAML usam as chaves ({,}`)` em sua sintaxe de atributo, que é a convenção pela qual um processador XAML reconhece que uma extensão de marcação deve processar o valor do atributo.</span><span class="sxs-lookup"><span data-stu-id="4c8ad-128">All markup extensions in XAML use the braces ({,}`)` in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute value.</span></span> <span data-ttu-id="4c8ad-129">Para obter mais informações sobre extensões de marcação em geral, consulte [conversores de tipo e extensões de marcação para XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="4c8ad-129">For more information about markup extensions in general, see [Type Converters and Markup Extensions for XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).</span></span>  
  
 <span data-ttu-id="4c8ad-130">XAML 2009, `x:Array` é definido como uma linguagem primitiva em vez de uma extensão de marcação.</span><span class="sxs-lookup"><span data-stu-id="4c8ad-130">In XAML 2009, `x:Array` is defined as a language primitive instead of a markup extension.</span></span> <span data-ttu-id="4c8ad-131">Para obter mais informações, consulte [tipos internos para primitivos de linguagem XAML comum](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="4c8ad-131">For more information, see [Built-in Types for Common XAML Language Primitives](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md).</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="4c8ad-132">Observações de uso do WPF</span><span class="sxs-lookup"><span data-stu-id="4c8ad-132">WPF Usage Notes</span></span>  
 <span data-ttu-id="4c8ad-133">Normalmente, os elementos de objeto que preenche um `x:Array` não são elementos que existem no [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] do namespace XAML e exigem um mapeamento de prefixo para um namespace XAML não padrão.</span><span class="sxs-lookup"><span data-stu-id="4c8ad-133">Typically, the object elements that populate an `x:Array` are not elements that exist in the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML namespace, and require a prefix mapping to a non-default XAML namespace.</span></span>  
  
 <span data-ttu-id="4c8ad-134">Por exemplo, o seguinte é uma matriz simples de duas cadeias de caracteres, com o `sys` prefixo (e também `x`) definidos no nível da matriz.</span><span class="sxs-lookup"><span data-stu-id="4c8ad-134">For example, the following is a simple array of two strings, with the `sys` prefix (and also `x`) defined at the level of the array.</span></span>  
  
 <span data-ttu-id="4c8ad-135">[xaml]</span><span class="sxs-lookup"><span data-stu-id="4c8ad-135">[xaml]</span></span>  
  
 `<x:Array Type="sys:String" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 `xmlns:sys="clr-namespace:System;assembly=mscorlib">`  
  
 `<sys:String>Hello</sys:String>`  
  
 `<sys:String>World</sys:String>`  
  
 `</x:Array>`  
  
 <span data-ttu-id="4c8ad-136">Para tipos personalizados que são usados como elementos de matriz, a classe também deve dar suporte aos requisitos de serem instanciados em XAML, como elementos de objeto.</span><span class="sxs-lookup"><span data-stu-id="4c8ad-136">For custom types that are used as array elements, the class must also support the requirements for being instantiated in XAML as object elements.</span></span> <span data-ttu-id="4c8ad-137">Para obter mais informações, consulte [XAML e Classes personalizadas para WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="4c8ad-137">For more information, see [XAML and Custom Classes for WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c8ad-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4c8ad-138">See Also</span></span>  
 [<span data-ttu-id="4c8ad-139">Extensões de marcação e XAML do WPF</span><span class="sxs-lookup"><span data-stu-id="4c8ad-139">Markup Extensions and WPF XAML</span></span>](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="4c8ad-140">Tipos migrados do WPF para System.Xaml</span><span class="sxs-lookup"><span data-stu-id="4c8ad-140">Types Migrated from WPF to System.Xaml</span></span>](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
