---
title: Extensão de marcação x:Type
ms.date: 03/30/2017
f1_keywords:
- x:TypeExtension
- Type
- x:Type
- xType
- TypeExtension
helpviewer_keywords:
- x:Type markup extension [XAML Services]
- XAML [XAML Services], x:Type markup extension
- XAML [XAML Services], TargetType attribute
- TargetType attribute [XAML Services]
- Type markup extension in XAML [XAML Services]
ms.assetid: e0e0ce6f-e873-49c7-8ad7-8b840eb353ec
ms.openlocfilehash: 00e6684f6ad1eb8d96f72f49bd5e0d211c8166c3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559064"
---
# <a name="xtype-markup-extension"></a><span data-ttu-id="dd97b-102">Extensão de marcação x:Type</span><span class="sxs-lookup"><span data-stu-id="dd97b-102">x:Type Markup Extension</span></span>

<span data-ttu-id="dd97b-103">Fornece o <xref:System.Type> objeto CLR que é o tipo subjacente para um tipo XAML especificado.</span><span class="sxs-lookup"><span data-stu-id="dd97b-103">Supplies the CLR <xref:System.Type> object that is the underlying type for a specified XAML type.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="dd97b-104">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="dd97b-104">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Type prefix:typeNameValue}" .../>
```

## <a name="xaml-object-element-usage"></a><span data-ttu-id="dd97b-105">Uso de elemento Object do XAML</span><span class="sxs-lookup"><span data-stu-id="dd97b-105">XAML Object Element Usage</span></span>

```xaml
<x:Type TypeName="prefix:typeNameValue"/>
```

## <a name="xaml-values"></a><span data-ttu-id="dd97b-106">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="dd97b-106">XAML Values</span></span>

|||
|-|-|
|`prefix`|<span data-ttu-id="dd97b-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="dd97b-107">Optional.</span></span> <span data-ttu-id="dd97b-108">Um prefixo que mapeia um namespace XAML não padrão.</span><span class="sxs-lookup"><span data-stu-id="dd97b-108">A prefix that maps a non-default XAML namespace.</span></span> <span data-ttu-id="dd97b-109">A especificação de um prefixo frequentemente não é necessária.</span><span class="sxs-lookup"><span data-stu-id="dd97b-109">Specifying a prefix is frequently not necessary.</span></span> <span data-ttu-id="dd97b-110">Consulte Observações.</span><span class="sxs-lookup"><span data-stu-id="dd97b-110">See Remarks.</span></span>|
|`typeNameValue`|<span data-ttu-id="dd97b-111">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="dd97b-111">Required.</span></span> <span data-ttu-id="dd97b-112">Um nome de tipo que possa ser resolvido para o namespace XAML padrão atual; ou o prefixo mapeado especificado se `prefix` for fornecido.</span><span class="sxs-lookup"><span data-stu-id="dd97b-112">A type name resolvable to the current default XAML namespace; or the specified mapped prefix if `prefix` is supplied.</span></span>|

## <a name="remarks"></a><span data-ttu-id="dd97b-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="dd97b-113">Remarks</span></span>

<span data-ttu-id="dd97b-114">A `x:Type` extensão de marcação tem uma função semelhante para o `typeof()` operador em C# ou o `GetType` operador no Microsoft Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="dd97b-114">The `x:Type` markup extension has a similar function to the `typeof()` operator in C# or the `GetType` operator in Microsoft Visual Basic.</span></span>

<span data-ttu-id="dd97b-115">A `x:Type` extensão de marcação fornece um comportamento de conversão de cadeia de caracteres para propriedades que usam o tipo <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="dd97b-115">The `x:Type` markup extension supplies a from-string conversion behavior for properties that take the type <xref:System.Type>.</span></span> <span data-ttu-id="dd97b-116">A entrada é um tipo XAML.</span><span class="sxs-lookup"><span data-stu-id="dd97b-116">The input is a XAML type.</span></span> <span data-ttu-id="dd97b-117">A relação entre o tipo XAML de entrada e o CLR de saída <xref:System.Type> é que a saída <xref:System.Type> é a <xref:System.Xaml.XamlType.UnderlyingType%2A> da entrada <xref:System.Xaml.XamlType> , depois de Pesquisar o necessário <xref:System.Xaml.XamlType> com base no contexto do esquema XAML e no <xref:System.Windows.Markup.IXamlTypeResolver> serviço que o contexto fornece.</span><span class="sxs-lookup"><span data-stu-id="dd97b-117">The relationship between the input XAML type and the output CLR <xref:System.Type> is that the output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input <xref:System.Xaml.XamlType>, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>

<span data-ttu-id="dd97b-118">Nos serviços XAML do .NET, o tratamento para essa extensão de marcação é definido pela <xref:System.Windows.Markup.TypeExtension> classe.</span><span class="sxs-lookup"><span data-stu-id="dd97b-118">In .NET XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.TypeExtension> class.</span></span>

<span data-ttu-id="dd97b-119">Em implementações de estrutura específicas, algumas propriedades que assumem <xref:System.Type> como um valor podem aceitar o nome do tipo diretamente (o valor da cadeia de caracteres do tipo `Name` ).</span><span class="sxs-lookup"><span data-stu-id="dd97b-119">In specific framework implementations, some properties that take <xref:System.Type> as a value can accept the name of the type directly (the string value of the type `Name`).</span></span> <span data-ttu-id="dd97b-120">No entanto, a implementação desse comportamento é um cenário complexo.</span><span class="sxs-lookup"><span data-stu-id="dd97b-120">However, implementing this behavior is a complex scenario.</span></span> <span data-ttu-id="dd97b-121">Para obter exemplos, consulte a seção "observações de uso do WPF" a seguir.</span><span class="sxs-lookup"><span data-stu-id="dd97b-121">For examples, see the "WPF Usage Notes" section that follows.</span></span>

<span data-ttu-id="dd97b-122">A sintaxe de atributo é a sintaxe mais comum usada com essa extensão de marcação.</span><span class="sxs-lookup"><span data-stu-id="dd97b-122">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="dd97b-123">O token da cadeia de caracteres fornecido após a cadeia de caracteres identificadora `x:Type` é atribuído como o valor <xref:System.Windows.Markup.TypeExtension.TypeName%2A> da classe de extensão subjacente <xref:System.Windows.Markup.TypeExtension>.</span><span class="sxs-lookup"><span data-stu-id="dd97b-123">The string token provided after the `x:Type` identifier string is assigned as the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> value of the underlying <xref:System.Windows.Markup.TypeExtension> extension class.</span></span> <span data-ttu-id="dd97b-124">No contexto de esquema XAML padrão para serviços XAML .NET, que é baseado em tipos CLR, o valor desse atributo é o <xref:System.Reflection.MemberInfo.Name%2A> do tipo desejado ou contém isso <xref:System.Reflection.MemberInfo.Name%2A> precedido por um prefixo para um mapeamento de namespace XAML não padrão.</span><span class="sxs-lookup"><span data-stu-id="dd97b-124">Under the default XAML schema context for .NET XAML Services, which is based on CLR types, the value of this attribute is either the <xref:System.Reflection.MemberInfo.Name%2A> of the desired type, or contains that <xref:System.Reflection.MemberInfo.Name%2A> preceded by a prefix for a non-default XAML namespace mapping.</span></span>

<span data-ttu-id="dd97b-125">A `x:Type` extensão de marcação pode ser usada na sintaxe do elemento de objeto.</span><span class="sxs-lookup"><span data-stu-id="dd97b-125">The `x:Type` markup extension can be used in object element syntax.</span></span> <span data-ttu-id="dd97b-126">Nesse caso, especificar o valor da <xref:System.Windows.Markup.TypeExtension.TypeName%2A> propriedade é necessário para inicializar corretamente a extensão.</span><span class="sxs-lookup"><span data-stu-id="dd97b-126">In this case, specifying the value of the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> property is required to properly initialize the extension.</span></span>

<span data-ttu-id="dd97b-127">A `x:Type` extensão de marcação também pode ser usada como um atributo detalhado; no entanto, esse uso não é típico: `<object property="{x:Type TypeName=typeNameValue}" .../>`</span><span class="sxs-lookup"><span data-stu-id="dd97b-127">The `x:Type` markup extension can also be used as a verbose attribute; however this use is not typical: `<object property="{x:Type TypeName=typeNameValue}" .../>`</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="dd97b-128">Notas de uso do WPF</span><span class="sxs-lookup"><span data-stu-id="dd97b-128">WPF Usage Notes</span></span>

### <a name="default-xaml-namespace-and-type-mapping"></a><span data-ttu-id="dd97b-129">Namespace XAML padrão e mapeamento de tipo</span><span class="sxs-lookup"><span data-stu-id="dd97b-129">Default XAML Namespace and Type Mapping</span></span>

<span data-ttu-id="dd97b-130">O namespace XAML padrão para a programação do WPF contém a maioria dos tipos XAML necessários para cenários típicos de XAML; Portanto, geralmente você pode evitar prefixos ao referenciar valores de tipo XAML.</span><span class="sxs-lookup"><span data-stu-id="dd97b-130">The default XAML namespace for WPF programming contains most of the XAML types you need for typical XAML scenarios; therefore, you can often avoid prefixes when referencing XAML type values.</span></span> <span data-ttu-id="dd97b-131">Talvez seja necessário mapear um prefixo se você estiver fazendo referência a um tipo de um assembly personalizado ou a tipos que existem em um assembly do WPF, mas que são de um namespace CLR que não foi mapeado para o namespace XAML padrão.</span><span class="sxs-lookup"><span data-stu-id="dd97b-131">You might need to map a prefix if you are referencing a type from a custom assembly or for types that exist in a WPF assembly but are from a CLR namespace that was not mapped to the default XAML namespace.</span></span> <span data-ttu-id="dd97b-132">Para obter mais informações sobre prefixos, namespaces XAML e mapeamento de namespaces CLR, consulte [namespaces XAML e mapeamento de namespace para WPF XAML](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml).</span><span class="sxs-lookup"><span data-stu-id="dd97b-132">For more information about prefixes, XAML namespaces, and mapping CLR namespaces, see [XAML Namespaces and Namespace Mapping for WPF XAML](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml).</span></span>

### <a name="type-properties-that-support-typename-as-string"></a><span data-ttu-id="dd97b-133">Propriedades de tipo que dão suporte a TypeName como cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="dd97b-133">Type Properties That Support Typename-as-String</span></span>

<span data-ttu-id="dd97b-134">O WPF dá suporte a técnicas que permitem especificar o valor de algumas propriedades do tipo <xref:System.Type> sem a necessidade de um `x:Type` uso de extensão de marcação.</span><span class="sxs-lookup"><span data-stu-id="dd97b-134">WPF supports techniques that enable specifying the value of some properties of type <xref:System.Type> without requiring an `x:Type` markup extension usage.</span></span> <span data-ttu-id="dd97b-135">Em vez disso, você pode especificar o valor como uma cadeia de caracteres que nomeia o tipo.</span><span class="sxs-lookup"><span data-stu-id="dd97b-135">Instead, you can specify the value as a string that names the type.</span></span> <span data-ttu-id="dd97b-136">Exemplos disso são <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> e <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="dd97b-136">Examples of this are <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> and <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="dd97b-137">O suporte para esse comportamento não é fornecido por meio de conversores de tipo ou extensões de marcação.</span><span class="sxs-lookup"><span data-stu-id="dd97b-137">Support for this behavior is not provided through either type converters or markup extensions.</span></span> <span data-ttu-id="dd97b-138">Em vez disso, esse é um comportamento de adiamento implementado por meio do <xref:System.Windows.FrameworkElementFactory> .</span><span class="sxs-lookup"><span data-stu-id="dd97b-138">Instead, this is a deferral behavior implemented through <xref:System.Windows.FrameworkElementFactory>.</span></span>

<span data-ttu-id="dd97b-139">O Silverlight dá suporte a uma convenção semelhante.</span><span class="sxs-lookup"><span data-stu-id="dd97b-139">Silverlight supports a similar convention.</span></span> <span data-ttu-id="dd97b-140">Na verdade, atualmente o Silverlight não dá suporte `{x:Type}` a seu suporte a idioma XAML e não aceita `{x:Type}` usos fora de algumas circunstâncias destinadas a oferecer suporte à migração de XAML do WPF-Silverlight.</span><span class="sxs-lookup"><span data-stu-id="dd97b-140">In fact, Silverlight does not currently support `{x:Type}` in its XAML language support, and does not accept `{x:Type}` usages outside of a few circumstances that are intended to support WPF-Silverlight XAML migration.</span></span> <span data-ttu-id="dd97b-141">Portanto, o comportamento de TypeName como cadeia de caracteres é interno a toda avaliação de propriedade nativa do Silverlight, em que um <xref:System.Type> é o valor.</span><span class="sxs-lookup"><span data-stu-id="dd97b-141">Therefore, the typename-as-string behavior is built-in to all Silverlight native property evaluation where a <xref:System.Type> is the value.</span></span>

## <a name="xaml-2009"></a><span data-ttu-id="dd97b-142">XAML 2009</span><span class="sxs-lookup"><span data-stu-id="dd97b-142">XAML 2009</span></span>

<span data-ttu-id="dd97b-143">O XAML 2009 fornece suporte adicional para tipos genéricos e modifica o comportamento do recurso do `x:TypeArguments` e `x:Type` para fornecer esse suporte.</span><span class="sxs-lookup"><span data-stu-id="dd97b-143">XAML 2009 provides additional support for generic types and modifies the feature behavior of `x:TypeArguments` and `x:Type` to provide this support.</span></span>

- <span data-ttu-id="dd97b-144">`x:TypeArguments` e o elemento Object associado para uma instanciação de objeto genérico pode estar em elementos que não sejam a raiz.</span><span class="sxs-lookup"><span data-stu-id="dd97b-144">`x:TypeArguments` and the associated object element for a generic object instantiation can be on elements other than the root.</span></span> <span data-ttu-id="dd97b-145">Para obter mais informações, consulte a seção "XAML 2009" da [diretiva x:TypeArguments](xtypearguments-directive.md).</span><span class="sxs-lookup"><span data-stu-id="dd97b-145">For more information, see the "XAML 2009" section of [x:TypeArguments Directive](xtypearguments-directive.md).</span></span>

- <span data-ttu-id="dd97b-146">O XAML 2009 dá suporte a uma sintaxe para especificar a restrição de um tipo genérico na marcação.</span><span class="sxs-lookup"><span data-stu-id="dd97b-146">XAML 2009 supports a syntax for specifying a generic type's constraint in markup.</span></span> <span data-ttu-id="dd97b-147">Isso pode ser usado pelo, `x:TypeArguments` por `x:Type` ou por dois recursos em combinação.</span><span class="sxs-lookup"><span data-stu-id="dd97b-147">This can be used by `x:TypeArguments`, by `x:Type`, or by the two features in combination.</span></span>

- <span data-ttu-id="dd97b-148">A implementação XAML do WPF ao processar XAML 2009 para Load também adiciona esse recurso ao comportamento de conversão de tipo implícito para determinadas propriedades de estrutura que usam Type <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="dd97b-148">WPF XAML implementation when processing XAML 2009 for load also adds this capability to the implicit type conversion behavior for certain framework properties that use type <xref:System.Type>.</span></span>

<span data-ttu-id="dd97b-149">No WPF, você pode usar os recursos do XAML 2009, mas apenas para XAML flexível (XAML que não é compilado por marcação).</span><span class="sxs-lookup"><span data-stu-id="dd97b-149">In WPF, you can use XAML 2009 features but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="dd97b-150">O XAML com compilação de marcação para WPF e a forma de BAML do XAML atualmente não dão suporte às palavras-chave e aos recursos do XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="dd97b-150">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>

## <a name="see-also"></a><span data-ttu-id="dd97b-151">Confira também</span><span class="sxs-lookup"><span data-stu-id="dd97b-151">See also</span></span>

- <xref:System.Windows.Style>
- [<span data-ttu-id="dd97b-152">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="dd97b-152">Styling and Templating</span></span>](../fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="dd97b-153">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="dd97b-153">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
- [<span data-ttu-id="dd97b-154">Extensões de marcação e XAML WPF</span><span class="sxs-lookup"><span data-stu-id="dd97b-154">Markup Extensions and WPF XAML</span></span>](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)
