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
# <a name="xtype-markup-extension"></a>Extensão de marcação x:Type

Fornece o objeto <xref:System.Type> CLR que é o tipo subjacente para um tipo XAML especificado.

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
|`prefix`|Opcional. Um prefixo que mapeia um namespace XAML não padrão. Especificar um prefixo não é frequentemente necessário. Consulte Observações.|
|`typeNameValue`|Obrigatórios. Um nome de tipo solucionável para o namespace XAML padrão atual; ou o prefixo mapeado especificado se `prefix` for fornecido.|

## <a name="remarks"></a>Comentários

A `x:Type` extensão de marcação `typeof()` tem uma função `GetType` semelhante à do operador em C# ou do operador no Microsoft Visual Basic.

A `x:Type` extensão de marcação fornece um comportamento de <xref:System.Type>conversão de string para propriedades que tomam o tipo . A entrada é do tipo XAML. A relação entre o tipo XAML <xref:System.Type> de entrada <xref:System.Type> e <xref:System.Xaml.XamlType.UnderlyingType%2A> a saída <xref:System.Xaml.XamlType>CLR é <xref:System.Xaml.XamlType> que a saída é a da <xref:System.Windows.Markup.IXamlTypeResolver> entrada, depois de procurar o necessário com base no contexto do esquema XAML e no serviço que o contexto fornece.

Nos Serviços XAML .NET, o manuseio desta extensão de marcação é definido pela <xref:System.Windows.Markup.TypeExtension> classe.

Em implementações específicas de framework, algumas propriedades que tomam <xref:System.Type> como valor podem aceitar `Name`o nome do tipo diretamente (o valor da seqüência do tipo ). No entanto, implementar esse comportamento é um cenário complexo. Por exemplo, consulte a seção "Notas de uso do WPF" a seguir.

A sintaxe de atributo é a sintaxe mais comum usada com essa extensão de marcação. O token da cadeia de caracteres fornecido após a cadeia de caracteres identificadora `x:Type` é atribuído como o valor <xref:System.Windows.Markup.TypeExtension.TypeName%2A> da classe de extensão subjacente <xref:System.Windows.Markup.TypeExtension>. No contexto padrão do esquema XAML para .NET XAML Services, que é baseado em <xref:System.Reflection.MemberInfo.Name%2A> tipos CLR, o valor <xref:System.Reflection.MemberInfo.Name%2A> deste atributo é o do tipo desejado ou contém aquele precedido por um prefixo para um mapeamento de namespace XAML não padrão.

A `x:Type` extensão de marcação pode ser usada na sintaxe do elemento objeto. Neste caso, especificar o <xref:System.Windows.Markup.TypeExtension.TypeName%2A> valor da propriedade é necessário para inicializar adequadamente a extensão.

A `x:Type` extensão de marcação também pode ser usada como um atributo verboso; no entanto, este uso não é típico:`<object property="{x:Type TypeName=typeNameValue}" .../>`

## <a name="wpf-usage-notes"></a>Notas de uso do WPF

### <a name="default-xaml-namespace-and-type-mapping"></a>Namespace e mapeamento de tipos padrão xaml

O namespace XAML padrão para programação WPF contém a maioria dos tipos XAML que você precisa para cenários típicos de XAML; portanto, muitas vezes você pode evitar prefixos ao referenciar valores do tipo XAML. Você pode precisar mapear um prefixo se estiver fazendo referência a um tipo de um conjunto personalizado ou para tipos que existem em um conjunto WPF, mas são de um namespace CLR que não foi mapeado para o namespace xaml padrão. Para obter mais informações sobre prefixos, namespaces XAML e mapeamento de namespaces CLR, consulte [XAML Namespaces e Namespace Mapping for WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).

### <a name="type-properties-that-support-typename-as-string"></a>Propriedades de tipo que suportam nome de tipo como string

O WPF suporta técnicas que permitem especificar <xref:System.Type> o `x:Type` valor de algumas propriedades do tipo sem exigir um uso de extensão de marcação. Em vez disso, você pode especificar o valor como uma string que nomeia o tipo. Exemplos disso são <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>e . O suporte para esse comportamento não é fornecido através de conversores de tipo ou extensões de marcação. Em vez disso, este é <xref:System.Windows.FrameworkElementFactory>um comportamento de adiamento implementado através de .

Silverlight apoia uma convenção semelhante. Na verdade, o Silverlight `{x:Type}` não suporta atualmente em seu suporte `{x:Type}` à linguagem XAML, e não aceita usos fora de algumas circunstâncias que se destinam a suportar a migração Do WPF-Silverlight XAML. Portanto, o comportamento de nome de tipo como string é incorporado a <xref:System.Type> toda avaliação de propriedade nativa silverlight onde a é o valor.

## <a name="xaml-2009"></a>XAML 2009

O XAML 2009 fornece suporte adicional para tipos `x:TypeArguments` `x:Type` genéricos e modifica o comportamento do recurso e para fornecer esse suporte.

- `x:TypeArguments`e o elemento objeto associado para uma instanciação de objeto genérico pode estar em elementos diferentes da raiz. Para obter mais informações, consulte a seção "XAML 2009" da [diretiva x:TypeArguments](xtypearguments-directive.md).

- XAML 2009 suporta uma sintaxe para especificar a restrição de um tipo genérico na marcação. Isso pode ser `x:TypeArguments`usado `x:Type`por , por , ou pelas duas características em combinação.

- A implementação do WPF XAML ao processar o XAML 2009 para carga também <xref:System.Type>adiciona esse recurso ao comportamento implícito de conversão de tipo para determinadas propriedades de framework que usam o tipo .

No WPF, você pode usar recursos XAML 2009, mas apenas para XAML solto (XAML que não é compilado por marcação). O XAML compilado por marcação para WPF e a forma BAML de XAML não suportam atualmente as palavras-chave e recursos do XAML 2009.

## <a name="see-also"></a>Confira também

- <xref:System.Windows.Style>
- [Estilo e modelagem](../fundamentals/styles-templates-overview.md)
- [Visão geral de XAML (WPF)](../fundamentals/xaml.md)
- [Extensões de marcação e XAML WPF](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
