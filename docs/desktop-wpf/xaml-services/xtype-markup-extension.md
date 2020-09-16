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
# <a name="xtype-markup-extension"></a>Extensão de marcação x:Type

Fornece o <xref:System.Type> objeto CLR que é o tipo subjacente para um tipo XAML especificado.

## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML

```xaml
<object property="{x:Type prefix:typeNameValue}" .../>
```

## <a name="xaml-object-element-usage"></a>Uso de elemento Object do XAML

```xaml
<x:Type TypeName="prefix:typeNameValue"/>
```

## <a name="xaml-values"></a>Valores XAML

|||
|-|-|
|`prefix`|Opcional. Um prefixo que mapeia um namespace XAML não padrão. A especificação de um prefixo frequentemente não é necessária. Consulte Observações.|
|`typeNameValue`|Obrigatórios. Um nome de tipo que possa ser resolvido para o namespace XAML padrão atual; ou o prefixo mapeado especificado se `prefix` for fornecido.|

## <a name="remarks"></a>Comentários

A `x:Type` extensão de marcação tem uma função semelhante para o `typeof()` operador em C# ou o `GetType` operador no Microsoft Visual Basic.

A `x:Type` extensão de marcação fornece um comportamento de conversão de cadeia de caracteres para propriedades que usam o tipo <xref:System.Type> . A entrada é um tipo XAML. A relação entre o tipo XAML de entrada e o CLR de saída <xref:System.Type> é que a saída <xref:System.Type> é a <xref:System.Xaml.XamlType.UnderlyingType%2A> da entrada <xref:System.Xaml.XamlType> , depois de Pesquisar o necessário <xref:System.Xaml.XamlType> com base no contexto do esquema XAML e no <xref:System.Windows.Markup.IXamlTypeResolver> serviço que o contexto fornece.

Nos serviços XAML do .NET, o tratamento para essa extensão de marcação é definido pela <xref:System.Windows.Markup.TypeExtension> classe.

Em implementações de estrutura específicas, algumas propriedades que assumem <xref:System.Type> como um valor podem aceitar o nome do tipo diretamente (o valor da cadeia de caracteres do tipo `Name` ). No entanto, a implementação desse comportamento é um cenário complexo. Para obter exemplos, consulte a seção "observações de uso do WPF" a seguir.

A sintaxe de atributo é a sintaxe mais comum usada com essa extensão de marcação. O token da cadeia de caracteres fornecido após a cadeia de caracteres identificadora `x:Type` é atribuído como o valor <xref:System.Windows.Markup.TypeExtension.TypeName%2A> da classe de extensão subjacente <xref:System.Windows.Markup.TypeExtension>. No contexto de esquema XAML padrão para serviços XAML .NET, que é baseado em tipos CLR, o valor desse atributo é o <xref:System.Reflection.MemberInfo.Name%2A> do tipo desejado ou contém isso <xref:System.Reflection.MemberInfo.Name%2A> precedido por um prefixo para um mapeamento de namespace XAML não padrão.

A `x:Type` extensão de marcação pode ser usada na sintaxe do elemento de objeto. Nesse caso, especificar o valor da <xref:System.Windows.Markup.TypeExtension.TypeName%2A> propriedade é necessário para inicializar corretamente a extensão.

A `x:Type` extensão de marcação também pode ser usada como um atributo detalhado; no entanto, esse uso não é típico: `<object property="{x:Type TypeName=typeNameValue}" .../>`

## <a name="wpf-usage-notes"></a>Notas de uso do WPF

### <a name="default-xaml-namespace-and-type-mapping"></a>Namespace XAML padrão e mapeamento de tipo

O namespace XAML padrão para a programação do WPF contém a maioria dos tipos XAML necessários para cenários típicos de XAML; Portanto, geralmente você pode evitar prefixos ao referenciar valores de tipo XAML. Talvez seja necessário mapear um prefixo se você estiver fazendo referência a um tipo de um assembly personalizado ou a tipos que existem em um assembly do WPF, mas que são de um namespace CLR que não foi mapeado para o namespace XAML padrão. Para obter mais informações sobre prefixos, namespaces XAML e mapeamento de namespaces CLR, consulte [namespaces XAML e mapeamento de namespace para WPF XAML](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml).

### <a name="type-properties-that-support-typename-as-string"></a>Propriedades de tipo que dão suporte a TypeName como cadeia de caracteres

O WPF dá suporte a técnicas que permitem especificar o valor de algumas propriedades do tipo <xref:System.Type> sem a necessidade de um `x:Type` uso de extensão de marcação. Em vez disso, você pode especificar o valor como uma cadeia de caracteres que nomeia o tipo. Exemplos disso são <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> e <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType> . O suporte para esse comportamento não é fornecido por meio de conversores de tipo ou extensões de marcação. Em vez disso, esse é um comportamento de adiamento implementado por meio do <xref:System.Windows.FrameworkElementFactory> .

O Silverlight dá suporte a uma convenção semelhante. Na verdade, atualmente o Silverlight não dá suporte `{x:Type}` a seu suporte a idioma XAML e não aceita `{x:Type}` usos fora de algumas circunstâncias destinadas a oferecer suporte à migração de XAML do WPF-Silverlight. Portanto, o comportamento de TypeName como cadeia de caracteres é interno a toda avaliação de propriedade nativa do Silverlight, em que um <xref:System.Type> é o valor.

## <a name="xaml-2009"></a>XAML 2009

O XAML 2009 fornece suporte adicional para tipos genéricos e modifica o comportamento do recurso do `x:TypeArguments` e `x:Type` para fornecer esse suporte.

- `x:TypeArguments` e o elemento Object associado para uma instanciação de objeto genérico pode estar em elementos que não sejam a raiz. Para obter mais informações, consulte a seção "XAML 2009" da [diretiva x:TypeArguments](xtypearguments-directive.md).

- O XAML 2009 dá suporte a uma sintaxe para especificar a restrição de um tipo genérico na marcação. Isso pode ser usado pelo, `x:TypeArguments` por `x:Type` ou por dois recursos em combinação.

- A implementação XAML do WPF ao processar XAML 2009 para Load também adiciona esse recurso ao comportamento de conversão de tipo implícito para determinadas propriedades de estrutura que usam Type <xref:System.Type> .

No WPF, você pode usar os recursos do XAML 2009, mas apenas para XAML flexível (XAML que não é compilado por marcação). O XAML com compilação de marcação para WPF e a forma de BAML do XAML atualmente não dão suporte às palavras-chave e aos recursos do XAML 2009.

## <a name="see-also"></a>Confira também

- <xref:System.Windows.Style>
- [Estilo e modelagem](../fundamentals/styles-templates-overview.md)
- [Visão geral de XAML (WPF)](../fundamentals/xaml.md)
- [Extensões de marcação e XAML WPF](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)
