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
ms.openlocfilehash: f75d4e30dc41bbce995e466466c96c1a2830949b
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071356"
---
# <a name="xtype-markup-extension"></a><span data-ttu-id="c911e-102">Extensão de marcação x:Type</span><span class="sxs-lookup"><span data-stu-id="c911e-102">x:Type Markup Extension</span></span>

<span data-ttu-id="c911e-103">Fornece o objeto <xref:System.Type> CLR que é o tipo subjacente para um tipo XAML especificado.</span><span class="sxs-lookup"><span data-stu-id="c911e-103">Supplies the CLR <xref:System.Type> object that is the underlying type for a specified XAML type.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="c911e-104">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="c911e-104">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Type prefix:typeNameValue}" .../>
```

## <a name="xaml-object-element-usage"></a><span data-ttu-id="c911e-105">Uso de elemento Object do XAML</span><span class="sxs-lookup"><span data-stu-id="c911e-105">XAML Object Element Usage</span></span>

```xaml
<x:Type TypeName="prefix:typeNameValue"/>
```

## <a name="xaml-values"></a><span data-ttu-id="c911e-106">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="c911e-106">XAML Values</span></span>

|||
|-|-|
|`prefix`|<span data-ttu-id="c911e-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="c911e-107">Optional.</span></span> <span data-ttu-id="c911e-108">Um prefixo que mapeia um namespace XAML não padrão.</span><span class="sxs-lookup"><span data-stu-id="c911e-108">A prefix that maps a non-default XAML namespace.</span></span> <span data-ttu-id="c911e-109">Especificar um prefixo não é frequentemente necessário.</span><span class="sxs-lookup"><span data-stu-id="c911e-109">Specifying a prefix is frequently not necessary.</span></span> <span data-ttu-id="c911e-110">Consulte Observações.</span><span class="sxs-lookup"><span data-stu-id="c911e-110">See Remarks.</span></span>|
|`typeNameValue`|<span data-ttu-id="c911e-111">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="c911e-111">Required.</span></span> <span data-ttu-id="c911e-112">Um nome de tipo solucionável para o namespace XAML padrão atual; ou o prefixo mapeado especificado se `prefix` for fornecido.</span><span class="sxs-lookup"><span data-stu-id="c911e-112">A type name resolvable to the current default XAML namespace; or the specified mapped prefix if `prefix` is supplied.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c911e-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="c911e-113">Remarks</span></span>

<span data-ttu-id="c911e-114">A `x:Type` extensão de marcação `typeof()` tem uma função `GetType` semelhante à do operador em C# ou do operador no Microsoft Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c911e-114">The `x:Type` markup extension has a similar function to the `typeof()` operator in C# or the `GetType` operator in Microsoft Visual Basic.</span></span>

<span data-ttu-id="c911e-115">A `x:Type` extensão de marcação fornece um comportamento de <xref:System.Type>conversão de string para propriedades que tomam o tipo .</span><span class="sxs-lookup"><span data-stu-id="c911e-115">The `x:Type` markup extension supplies a from-string conversion behavior for properties that take the type <xref:System.Type>.</span></span> <span data-ttu-id="c911e-116">A entrada é do tipo XAML.</span><span class="sxs-lookup"><span data-stu-id="c911e-116">The input is a XAML type.</span></span> <span data-ttu-id="c911e-117">A relação entre o tipo XAML <xref:System.Type> de entrada <xref:System.Type> e <xref:System.Xaml.XamlType.UnderlyingType%2A> a saída <xref:System.Xaml.XamlType>CLR é <xref:System.Xaml.XamlType> que a saída é a da <xref:System.Windows.Markup.IXamlTypeResolver> entrada, depois de procurar o necessário com base no contexto do esquema XAML e no serviço que o contexto fornece.</span><span class="sxs-lookup"><span data-stu-id="c911e-117">The relationship between the input XAML type and the output CLR <xref:System.Type> is that the output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input <xref:System.Xaml.XamlType>, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>

<span data-ttu-id="c911e-118">Nos Serviços XAML .NET, o manuseio desta extensão de marcação é definido pela <xref:System.Windows.Markup.TypeExtension> classe.</span><span class="sxs-lookup"><span data-stu-id="c911e-118">In .NET XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.TypeExtension> class.</span></span>

<span data-ttu-id="c911e-119">Em implementações específicas de framework, algumas propriedades que tomam <xref:System.Type> como valor podem aceitar `Name`o nome do tipo diretamente (o valor da seqüência do tipo ).</span><span class="sxs-lookup"><span data-stu-id="c911e-119">In specific framework implementations, some properties that take <xref:System.Type> as a value can accept the name of the type directly (the string value of the type `Name`).</span></span> <span data-ttu-id="c911e-120">No entanto, implementar esse comportamento é um cenário complexo.</span><span class="sxs-lookup"><span data-stu-id="c911e-120">However, implementing this behavior is a complex scenario.</span></span> <span data-ttu-id="c911e-121">Por exemplo, consulte a seção "Notas de uso do WPF" a seguir.</span><span class="sxs-lookup"><span data-stu-id="c911e-121">For examples, see the "WPF Usage Notes" section that follows.</span></span>

<span data-ttu-id="c911e-122">A sintaxe de atributo é a sintaxe mais comum usada com essa extensão de marcação.</span><span class="sxs-lookup"><span data-stu-id="c911e-122">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="c911e-123">O token da cadeia de caracteres fornecido após a cadeia de caracteres identificadora `x:Type` é atribuído como o valor <xref:System.Windows.Markup.TypeExtension.TypeName%2A> da classe de extensão subjacente <xref:System.Windows.Markup.TypeExtension>.</span><span class="sxs-lookup"><span data-stu-id="c911e-123">The string token provided after the `x:Type` identifier string is assigned as the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> value of the underlying <xref:System.Windows.Markup.TypeExtension> extension class.</span></span> <span data-ttu-id="c911e-124">No contexto padrão do esquema XAML para .NET XAML Services, que é baseado em <xref:System.Reflection.MemberInfo.Name%2A> tipos CLR, o valor <xref:System.Reflection.MemberInfo.Name%2A> deste atributo é o do tipo desejado ou contém aquele precedido por um prefixo para um mapeamento de namespace XAML não padrão.</span><span class="sxs-lookup"><span data-stu-id="c911e-124">Under the default XAML schema context for .NET XAML Services, which is based on CLR types, the value of this attribute is either the <xref:System.Reflection.MemberInfo.Name%2A> of the desired type, or contains that <xref:System.Reflection.MemberInfo.Name%2A> preceded by a prefix for a non-default XAML namespace mapping.</span></span>

<span data-ttu-id="c911e-125">A `x:Type` extensão de marcação pode ser usada na sintaxe do elemento objeto.</span><span class="sxs-lookup"><span data-stu-id="c911e-125">The `x:Type` markup extension can be used in object element syntax.</span></span> <span data-ttu-id="c911e-126">Neste caso, especificar o <xref:System.Windows.Markup.TypeExtension.TypeName%2A> valor da propriedade é necessário para inicializar adequadamente a extensão.</span><span class="sxs-lookup"><span data-stu-id="c911e-126">In this case, specifying the value of the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> property is required to properly initialize the extension.</span></span>

<span data-ttu-id="c911e-127">A `x:Type` extensão de marcação também pode ser usada como um atributo verboso; no entanto, este uso não é típico:`<object property="{x:Type TypeName=typeNameValue}" .../>`</span><span class="sxs-lookup"><span data-stu-id="c911e-127">The `x:Type` markup extension can also be used as a verbose attribute; however this use is not typical: `<object property="{x:Type TypeName=typeNameValue}" .../>`</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="c911e-128">Notas de uso do WPF</span><span class="sxs-lookup"><span data-stu-id="c911e-128">WPF Usage Notes</span></span>

### <a name="default-xaml-namespace-and-type-mapping"></a><span data-ttu-id="c911e-129">Namespace e mapeamento de tipos padrão xaml</span><span class="sxs-lookup"><span data-stu-id="c911e-129">Default XAML Namespace and Type Mapping</span></span>

<span data-ttu-id="c911e-130">O namespace XAML padrão para programação WPF contém a maioria dos tipos XAML que você precisa para cenários típicos de XAML; portanto, muitas vezes você pode evitar prefixos ao referenciar valores do tipo XAML.</span><span class="sxs-lookup"><span data-stu-id="c911e-130">The default XAML namespace for WPF programming contains most of the XAML types you need for typical XAML scenarios; therefore, you can often avoid prefixes when referencing XAML type values.</span></span> <span data-ttu-id="c911e-131">Você pode precisar mapear um prefixo se estiver fazendo referência a um tipo de um conjunto personalizado ou para tipos que existem em um conjunto WPF, mas são de um namespace CLR que não foi mapeado para o namespace xaml padrão.</span><span class="sxs-lookup"><span data-stu-id="c911e-131">You might need to map a prefix if you are referencing a type from a custom assembly or for types that exist in a WPF assembly but are from a CLR namespace that was not mapped to the default XAML namespace.</span></span> <span data-ttu-id="c911e-132">Para obter mais informações sobre prefixos, namespaces XAML e mapeamento de namespaces CLR, consulte [XAML Namespaces e Namespace Mapping for WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="c911e-132">For more information about prefixes, XAML namespaces, and mapping CLR namespaces, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span></span>

### <a name="type-properties-that-support-typename-as-string"></a><span data-ttu-id="c911e-133">Propriedades de tipo que suportam nome de tipo como string</span><span class="sxs-lookup"><span data-stu-id="c911e-133">Type Properties That Support Typename-as-String</span></span>

<span data-ttu-id="c911e-134">O WPF suporta técnicas que permitem especificar <xref:System.Type> o `x:Type` valor de algumas propriedades do tipo sem exigir um uso de extensão de marcação.</span><span class="sxs-lookup"><span data-stu-id="c911e-134">WPF supports techniques that enable specifying the value of some properties of type <xref:System.Type> without requiring an `x:Type` markup extension usage.</span></span> <span data-ttu-id="c911e-135">Em vez disso, você pode especificar o valor como uma string que nomeia o tipo.</span><span class="sxs-lookup"><span data-stu-id="c911e-135">Instead, you can specify the value as a string that names the type.</span></span> <span data-ttu-id="c911e-136">Exemplos disso são <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>e .</span><span class="sxs-lookup"><span data-stu-id="c911e-136">Examples of this are <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> and <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c911e-137">O suporte para esse comportamento não é fornecido através de conversores de tipo ou extensões de marcação.</span><span class="sxs-lookup"><span data-stu-id="c911e-137">Support for this behavior is not provided through either type converters or markup extensions.</span></span> <span data-ttu-id="c911e-138">Em vez disso, este é <xref:System.Windows.FrameworkElementFactory>um comportamento de adiamento implementado através de .</span><span class="sxs-lookup"><span data-stu-id="c911e-138">Instead, this is a deferral behavior implemented through <xref:System.Windows.FrameworkElementFactory>.</span></span>

<span data-ttu-id="c911e-139">Silverlight apoia uma convenção semelhante.</span><span class="sxs-lookup"><span data-stu-id="c911e-139">Silverlight supports a similar convention.</span></span> <span data-ttu-id="c911e-140">Na verdade, o Silverlight `{x:Type}` não suporta atualmente em seu suporte `{x:Type}` à linguagem XAML, e não aceita usos fora de algumas circunstâncias que se destinam a suportar a migração Do WPF-Silverlight XAML.</span><span class="sxs-lookup"><span data-stu-id="c911e-140">In fact, Silverlight does not currently support `{x:Type}` in its XAML language support, and does not accept `{x:Type}` usages outside of a few circumstances that are intended to support WPF-Silverlight XAML migration.</span></span> <span data-ttu-id="c911e-141">Portanto, o comportamento de nome de tipo como string é incorporado a <xref:System.Type> toda avaliação de propriedade nativa silverlight onde a é o valor.</span><span class="sxs-lookup"><span data-stu-id="c911e-141">Therefore, the typename-as-string behavior is built-in to all Silverlight native property evaluation where a <xref:System.Type> is the value.</span></span>

## <a name="xaml-2009"></a><span data-ttu-id="c911e-142">XAML 2009</span><span class="sxs-lookup"><span data-stu-id="c911e-142">XAML 2009</span></span>

<span data-ttu-id="c911e-143">O XAML 2009 fornece suporte adicional para tipos `x:TypeArguments` `x:Type` genéricos e modifica o comportamento do recurso e para fornecer esse suporte.</span><span class="sxs-lookup"><span data-stu-id="c911e-143">XAML 2009 provides additional support for generic types and modifies the feature behavior of `x:TypeArguments` and `x:Type` to provide this support.</span></span>

- <span data-ttu-id="c911e-144">`x:TypeArguments`e o elemento objeto associado para uma instanciação de objeto genérico pode estar em elementos diferentes da raiz.</span><span class="sxs-lookup"><span data-stu-id="c911e-144">`x:TypeArguments` and the associated object element for a generic object instantiation can be on elements other than the root.</span></span> <span data-ttu-id="c911e-145">Para obter mais informações, consulte a seção "XAML 2009" da [diretiva x:TypeArguments](xtypearguments-directive.md).</span><span class="sxs-lookup"><span data-stu-id="c911e-145">For more information, see the "XAML 2009" section of [x:TypeArguments Directive](xtypearguments-directive.md).</span></span>

- <span data-ttu-id="c911e-146">XAML 2009 suporta uma sintaxe para especificar a restrição de um tipo genérico na marcação.</span><span class="sxs-lookup"><span data-stu-id="c911e-146">XAML 2009 supports a syntax for specifying a generic type's constraint in markup.</span></span> <span data-ttu-id="c911e-147">Isso pode ser `x:TypeArguments`usado `x:Type`por , por , ou pelas duas características em combinação.</span><span class="sxs-lookup"><span data-stu-id="c911e-147">This can be used by `x:TypeArguments`, by `x:Type`, or by the two features in combination.</span></span>

- <span data-ttu-id="c911e-148">A implementação do WPF XAML ao processar o XAML 2009 para carga também <xref:System.Type>adiciona esse recurso ao comportamento implícito de conversão de tipo para determinadas propriedades de framework que usam o tipo .</span><span class="sxs-lookup"><span data-stu-id="c911e-148">WPF XAML implementation when processing XAML 2009 for load also adds this capability to the implicit type conversion behavior for certain framework properties that use type <xref:System.Type>.</span></span>

<span data-ttu-id="c911e-149">No WPF, você pode usar recursos XAML 2009, mas apenas para XAML solto (XAML que não é compilado por marcação).</span><span class="sxs-lookup"><span data-stu-id="c911e-149">In WPF, you can use XAML 2009 features but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="c911e-150">O XAML compilado por marcação para WPF e a forma BAML de XAML não suportam atualmente as palavras-chave e recursos do XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="c911e-150">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>

## <a name="see-also"></a><span data-ttu-id="c911e-151">Confira também</span><span class="sxs-lookup"><span data-stu-id="c911e-151">See also</span></span>

- <xref:System.Windows.Style>
- [<span data-ttu-id="c911e-152">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="c911e-152">Styling and Templating</span></span>](../fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="c911e-153">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="c911e-153">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
- [<span data-ttu-id="c911e-154">Extensões de marcação e XAML WPF</span><span class="sxs-lookup"><span data-stu-id="c911e-154">Markup Extensions and WPF XAML</span></span>](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
