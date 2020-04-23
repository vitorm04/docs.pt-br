---
title: Extensão de marcação x:Static
ms.date: 03/30/2017
f1_keywords:
- StaticExtension
- xStatic
- x:Static
helpviewer_keywords:
- x:Static markup extension [XAML Services]
- Static markup extension in XAML [XAML Services]
- XAML [XAML Services], x:Static markup extension
ms.assetid: 056aee79-7cdd-434f-8174-dfc856cad343
ms.openlocfilehash: fb9ee6807135f17fd9e0c799533bba28b369ebe2
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072021"
---
# <a name="xstatic-markup-extension"></a><span data-ttu-id="615d1-102">Extensão de marcação x:Static</span><span class="sxs-lookup"><span data-stu-id="615d1-102">x:Static Markup Extension</span></span>

<span data-ttu-id="615d1-103">Faz referência a qualquer entidade de código de valor estático que seja definida de forma compatível com a Especificação de Linguagem Comum (CLS).</span><span class="sxs-lookup"><span data-stu-id="615d1-103">References any static by-value code entity that is defined in a Common Language Specification (CLS)–compliant way.</span></span> <span data-ttu-id="615d1-104">A propriedade estática que é referenciada pode ser usada para fornecer o valor de uma propriedade em XAML.</span><span class="sxs-lookup"><span data-stu-id="615d1-104">The static property that is referenced can be used to provide the value of a property in XAML.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="615d1-105">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="615d1-105">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Static prefix:typeName.staticMemberName}" .../>
```

## <a name="xaml-values"></a><span data-ttu-id="615d1-106">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="615d1-106">XAML Values</span></span>

| | |
|-|-|
|`prefix`|<span data-ttu-id="615d1-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="615d1-107">Optional.</span></span> <span data-ttu-id="615d1-108">Um prefixo que se refere a um espaço de nome XAML mapeado e não padrão.</span><span class="sxs-lookup"><span data-stu-id="615d1-108">A prefix that refers to a mapped, non-default XAML namespace.</span></span> <span data-ttu-id="615d1-109">`prefix`é mostrado explicitamente no uso porque você raramente referencia propriedades estáticas que vêm de um namespace XAML padrão.</span><span class="sxs-lookup"><span data-stu-id="615d1-109">`prefix` is shown explicitly in the usage because you rarely reference static properties that come from a default XAML namespace.</span></span> <span data-ttu-id="615d1-110">Consulte Observações.</span><span class="sxs-lookup"><span data-stu-id="615d1-110">See Remarks.</span></span>|
|`typeName`|<span data-ttu-id="615d1-111">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="615d1-111">Required.</span></span> <span data-ttu-id="615d1-112">O nome do tipo que define o membro estático desejado.</span><span class="sxs-lookup"><span data-stu-id="615d1-112">The name of the type that defines the desired static member.</span></span>|
|`staticMemberName`|<span data-ttu-id="615d1-113">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="615d1-113">Required.</span></span> <span data-ttu-id="615d1-114">O nome do membro de valor estático desejado (uma constante, uma propriedade estática, um campo ou um valor de enumeração).</span><span class="sxs-lookup"><span data-stu-id="615d1-114">The name of the desired static value member (a constant, a static property, a field, or an enumeration value).</span></span>|

## <a name="remarks"></a><span data-ttu-id="615d1-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="615d1-115">Remarks</span></span>

<span data-ttu-id="615d1-116">A entidade de código que é referenciada deve ser uma das seguintes:</span><span class="sxs-lookup"><span data-stu-id="615d1-116">The code entity that is referenced must be one of the following:</span></span>

- <span data-ttu-id="615d1-117">Uma constante</span><span class="sxs-lookup"><span data-stu-id="615d1-117">A constant</span></span>
- <span data-ttu-id="615d1-118">Uma propriedade estática</span><span class="sxs-lookup"><span data-stu-id="615d1-118">A static property</span></span>
- <span data-ttu-id="615d1-119">Um campo</span><span class="sxs-lookup"><span data-stu-id="615d1-119">A field</span></span>
- <span data-ttu-id="615d1-120">Um valor de enumeração</span><span class="sxs-lookup"><span data-stu-id="615d1-120">An enumeration value</span></span>

<span data-ttu-id="615d1-121">Especificar qualquer outra entidade de código, como uma propriedade não estática, causa um erro de tempo de compilação se o XAML for compilado ou uma exceção de análise de tempo de carga XAML.</span><span class="sxs-lookup"><span data-stu-id="615d1-121">Specifying any other code entity, such as a nonstatic property, causes a compile-time error if the XAML is markup compiled, or a XAML load-time parse exception.</span></span>

<span data-ttu-id="615d1-122">Você pode `x:Static` fazer referências a campos estáticos ou propriedades que não estejam no namespace XAML padrão para o documento XAML atual; no entanto, isso requer um mapeamento de prefixo.</span><span class="sxs-lookup"><span data-stu-id="615d1-122">You can make `x:Static` references to static fields or properties that are not in the default XAML namespace for the current XAML document; however, this requires a prefix mapping.</span></span> <span data-ttu-id="615d1-123">Os namespaces XAML são quase sempre definidos no elemento raiz do documento XAML.</span><span class="sxs-lookup"><span data-stu-id="615d1-123">XAML namespaces are almost always defined on the root element of the XAML document.</span></span>

<span data-ttu-id="615d1-124">As operações de pesquisa para propriedades estáticas podem ser realizadas pela .NET XAML Services e seus leitores XAML e escritores XAML, quando estão sendo executados com o contexto padrão do esquema XAML.</span><span class="sxs-lookup"><span data-stu-id="615d1-124">The lookup operations for static properties can be performed by .NET XAML Services and its XAML readers and XAML writers, when they are running with the default XAML schema context.</span></span> <span data-ttu-id="615d1-125">Este contexto de esquema XAML pode usar a reflexão CLR para fornecer os valores estáticos necessários para a construção de gráficos de objetos.</span><span class="sxs-lookup"><span data-stu-id="615d1-125">This XAML schema context can use CLR reflection to provide the necessary static values for object graph construction.</span></span> <span data-ttu-id="615d1-126">O `typeName` que você especifica é na verdade um nome de tipo XAML, não um nome de tipo CLR, embora estes sejam essencialmente o mesmo nome ao usar o contexto padrão do esquema XAML ou ao usar todas as estruturas de implementação XAML baseadas em CLR existentes.</span><span class="sxs-lookup"><span data-stu-id="615d1-126">The `typeName` you specify is actually a XAML type name, not a CLR type name, although these are essentially the same name when using the default XAML schema context or when using all existing CLR-based XAML-implementing frameworks.</span></span>

<span data-ttu-id="615d1-127">Tenha cuidado ao `x:Static` fazer referências que não são diretamente o tipo de valor de um imóvel.</span><span class="sxs-lookup"><span data-stu-id="615d1-127">Use caution when you make `x:Static` references that are not directly the type of a property's value.</span></span> <span data-ttu-id="615d1-128">Na seqüência de processamento XAML, os valores fornecidos de uma extensão de marcação não invocam conversão de valor adicional.</span><span class="sxs-lookup"><span data-stu-id="615d1-128">In the XAML processing sequence, provided values from a markup extension do not invoke additional value conversion.</span></span> <span data-ttu-id="615d1-129">Isso é verdade `x:Static` mesmo se sua referência criar uma seqüência de texto, e uma conversão de valor para valores de atributo com base na seqüência de texto normalmente ocorre para esse membro específico ou para quaisquer valores membros do tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="615d1-129">This is true even if your `x:Static` reference creates a text string, and a value conversion for attribute values based on text string typically occurs either for that specific member or for any member values of the return type.</span></span>

<span data-ttu-id="615d1-130">A sintaxe de atributo é a sintaxe mais comum usada com essa extensão de marcação.</span><span class="sxs-lookup"><span data-stu-id="615d1-130">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="615d1-131">O token da cadeia de caracteres fornecido após a cadeia de caracteres identificadora `x:Static` é atribuído como o valor <xref:System.Windows.Markup.StaticExtension.Member%2A> da classe de extensão subjacente <xref:System.Windows.Markup.StaticExtension>.</span><span class="sxs-lookup"><span data-stu-id="615d1-131">The string token provided after the `x:Static` identifier string is assigned as the <xref:System.Windows.Markup.StaticExtension.Member%2A> value of the underlying <xref:System.Windows.Markup.StaticExtension> extension class.</span></span>

<span data-ttu-id="615d1-132">Existem dois outros usos XAML que são tecnicamente possíveis.</span><span class="sxs-lookup"><span data-stu-id="615d1-132">There are two other XAML usages that are technically possible.</span></span> <span data-ttu-id="615d1-133">No entanto, esses usos são menos comuns porque são desnecessariamente verbosos:</span><span class="sxs-lookup"><span data-stu-id="615d1-133">However, these usages are less common because they are unnecessarily verbose:</span></span>

01. <span data-ttu-id="615d1-134">Sintaxe do elemento objeto.</span><span class="sxs-lookup"><span data-stu-id="615d1-134">Object element syntax.</span></span>

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

02. <span data-ttu-id="615d1-135">Sintaxe de atributo com propriedade membro explícita para seqüência de inicialização.</span><span class="sxs-lookup"><span data-stu-id="615d1-135">Attribute syntax with explicit Member property for initialization string.</span></span>

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

<span data-ttu-id="615d1-136">Na implementação do .NET XAML Services, o manuseio <xref:System.Windows.Markup.StaticExtension> dessa extensão de marcação é definido pela classe.</span><span class="sxs-lookup"><span data-stu-id="615d1-136">In .NET XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.StaticExtension> class.</span></span>

<span data-ttu-id="615d1-137">`x:Static` é uma extensão da marcação.</span><span class="sxs-lookup"><span data-stu-id="615d1-137">`x:Static` is a markup extension.</span></span> <span data-ttu-id="615d1-138">Todas as extensões de marcação `{` `}` em XAML usam os caracteres em sua sintaxe de atributos, que é a convenção pela qual um processador XAML reconhece que uma extensão de marcação deve fornecer um valor.</span><span class="sxs-lookup"><span data-stu-id="615d1-138">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must provide a value.</span></span> <span data-ttu-id="615d1-139">Para obter mais informações sobre extensões de marcação, consulte [Extensões de marcação para visão geral XAML](markup-extensions-overview.md).</span><span class="sxs-lookup"><span data-stu-id="615d1-139">For more information about markup extensions, see [Markup Extensions for XAML Overview](markup-extensions-overview.md).</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="615d1-140">Notas de uso do WPF</span><span class="sxs-lookup"><span data-stu-id="615d1-140">WPF Usage Notes</span></span>

<span data-ttu-id="615d1-141">O namespace XAML padrão que você usa para programação WPF não contém muitas propriedades estáticas úteis, e `{x:Static}` a maioria das propriedades estáticas úteis têm suporte, como conversores de tipo que facilitam o uso sem necessidade .</span><span class="sxs-lookup"><span data-stu-id="615d1-141">The default XAML namespace you use for WPF programming does not contain many useful static properties, and most of the useful static properties have support such as type converters that facilitate the usage without requiring `{x:Static}` .</span></span> <span data-ttu-id="615d1-142">Para propriedades estáticas, você deve mapear um prefixo para um namespace XAML se um dos seguintes for verdadeiro:</span><span class="sxs-lookup"><span data-stu-id="615d1-142">For static properties, you must map a prefix for a XAML namespace if one of the following is true:</span></span>

- <span data-ttu-id="615d1-143">Você está fazendo referência a um tipo que existe no WPF, mas não`http://schemas.microsoft.com/winfx/2006/xaml/presentation`faz parte do namespace XAML padrão para WPF ( ).</span><span class="sxs-lookup"><span data-stu-id="615d1-143">You are referencing a type that exists in WPF but is not part of the default XAML namespace for WPF (`http://schemas.microsoft.com/winfx/2006/xaml/presentation`).</span></span> <span data-ttu-id="615d1-144">Este é um cenário bastante `x:Static`comum para o uso .</span><span class="sxs-lookup"><span data-stu-id="615d1-144">This is a fairly common scenario for using `x:Static`.</span></span> <span data-ttu-id="615d1-145">Por exemplo, você `x:Static` pode usar uma referência com um <xref:System> mapeamento de namespace XAML para o namespace <xref:System.Environment> clr e o conjunto mscorlib, a fim de referenciar as propriedades estáticas da classe.</span><span class="sxs-lookup"><span data-stu-id="615d1-145">For example, you might use an `x:Static` reference with a XAML namespace mapping to the <xref:System> CLR namespace and mscorlib assembly in order to reference the static properties of the <xref:System.Environment> class.</span></span>

- <span data-ttu-id="615d1-146">Você está fazendo referência a um tipo de uma montagem personalizada.</span><span class="sxs-lookup"><span data-stu-id="615d1-146">You are referencing a type from a custom assembly.</span></span>

- <span data-ttu-id="615d1-147">Você está fazendo referência a um tipo que existe em um conjunto WPF, mas esse tipo está dentro de um namespace CLR que não foi mapeado para fazer parte do namespace Padrão XAML do WPF.</span><span class="sxs-lookup"><span data-stu-id="615d1-147">You are referencing a type that exists in a WPF assembly, but that type is within a CLR namespace that was not mapped to be part of the WPF default XAML namespace.</span></span> <span data-ttu-id="615d1-148">O mapeamento de namespaces CLR no namespace padrão xaml para WPF é realizado por definições nos vários conjuntos WPF (para obter mais informações sobre esse conceito, consulte [XAML Namespaces e Namespace Mapping for WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)).</span><span class="sxs-lookup"><span data-stu-id="615d1-148">The mapping of CLR namespaces into the default XAML namespace for WPF is performed by definitions in the various WPF assemblies (for more information about this concept, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)).</span></span> <span data-ttu-id="615d1-149">Os namespaces CLR não mapeados podem existir se esse namespace CLR for composto principalmente de <xref:System.Windows.Threading>definições de classe que não são tipicamente destinadas a XAML, tais como .</span><span class="sxs-lookup"><span data-stu-id="615d1-149">Non-mapped CLR namespaces can exist if that CLR namespace is composed mostly of class definitions that are not typically intended for XAML, such as <xref:System.Windows.Threading>.</span></span>

<span data-ttu-id="615d1-150">Para obter mais informações sobre como usar prefixos e namespaces XAML para WPF, consulte [XAML Namespaces e Namespace Mapping for WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="615d1-150">For more information on how to use prefixes and XAML namespaces for WPF, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="615d1-151">Confira também</span><span class="sxs-lookup"><span data-stu-id="615d1-151">See also</span></span>

- [<span data-ttu-id="615d1-152">Extensão de marcação x:Type</span><span class="sxs-lookup"><span data-stu-id="615d1-152">x:Type Markup Extension</span></span>](xtype-markup-extension.md)
- [<span data-ttu-id="615d1-153">Tipos migrados do WPF para System.Xaml</span><span class="sxs-lookup"><span data-stu-id="615d1-153">Types Migrated from WPF to System.Xaml</span></span>](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
