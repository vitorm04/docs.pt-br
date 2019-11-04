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
ms.openlocfilehash: df0b3fe53cb8f284fc6e2d79a9b2cea86318d701
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459921"
---
# <a name="xtype-markup-extension"></a>Extensão de marcação x:Type
Fornece o objeto CLR <xref:System.Type> que é o tipo subjacente para um tipo XAML especificado.  
  
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
|`typeNameValue`|Necessário. Um nome de tipo que possa ser resolvido para o namespace XAML padrão atual; ou o prefixo mapeado especificado se `prefix` for fornecido.|  
  
## <a name="remarks"></a>Comentários  
 A extensão de marcação de `x:Type` tem uma função semelhante ao operador de C# `typeof()` no ou no operador de `GetType` no Microsoft Visual Basic.  
  
 A extensão de marcação de `x:Type` fornece um comportamento de conversão de cadeia de caracteres para propriedades que usam o tipo <xref:System.Type>. A entrada é um tipo XAML. A relação entre o tipo XAML de entrada e o CLR de saída <xref:System.Type> é que a <xref:System.Type> de saída é a <xref:System.Xaml.XamlType.UnderlyingType%2A> do <xref:System.Xaml.XamlType>de entrada, depois de Pesquisar o <xref:System.Xaml.XamlType> necessário com base no contexto de esquema XAML e no serviço de <xref:System.Windows.Markup.IXamlTypeResolver> que o contexto fornece.  
  
 Em .NET Framework serviços XAML, o tratamento para essa extensão de marcação é definido pela classe <xref:System.Windows.Markup.TypeExtension>.  
  
 Em implementações de estrutura específicas, algumas propriedades que levam <xref:System.Type> como um valor podem aceitar o nome do tipo diretamente (o valor da cadeia de caracteres do tipo `Name`). No entanto, a implementação desse comportamento é um cenário complexo. Para obter exemplos, consulte a seção "observações de uso do WPF" a seguir.  
  
 A sintaxe de atributo é a sintaxe mais comum usada com essa extensão de marcação. O token da cadeia de caracteres fornecido após a cadeia de caracteres identificadora `x:Type` é atribuído como o valor <xref:System.Windows.Markup.TypeExtension.TypeName%2A> da classe de extensão subjacente <xref:System.Windows.Markup.TypeExtension>. No contexto de esquema XAML padrão para .NET Framework serviços XAML, que é baseado em tipos CLR, o valor desse atributo é o <xref:System.Reflection.MemberInfo.Name%2A> do tipo desejado ou contém esse <xref:System.Reflection.MemberInfo.Name%2A> precedido por um prefixo para um mapeamento de namespace XAML não padrão.  
  
 A extensão de marcação de `x:Type` pode ser usada na sintaxe do elemento de objeto. Nesse caso, especificar o valor da propriedade <xref:System.Windows.Markup.TypeExtension.TypeName%2A> é necessário para inicializar corretamente a extensão.  
  
 A extensão de marcação de `x:Type` também pode ser usada como um atributo detalhado; no entanto, esse uso não é típico: `<object property="{x:Type TypeName=typeNameValue}" .../>`  
  
## <a name="wpf-usage-notes"></a>Observações de uso do WPF  
  
### <a name="default-xaml-namespace-and-type-mapping"></a>Namespace XAML padrão e mapeamento de tipo  
 O namespace XAML padrão para a programação do WPF contém a maioria dos tipos XAML necessários para cenários típicos de XAML; Portanto, geralmente você pode evitar prefixos ao referenciar valores de tipo XAML. Talvez seja necessário mapear um prefixo se você estiver fazendo referência a um tipo de um assembly personalizado ou a tipos que existem em um assembly do WPF, mas que são de um namespace CLR que não foi mapeado para o namespace XAML padrão. Para obter mais informações sobre prefixos, namespaces XAML e mapeamento de namespaces CLR, consulte [namespaces XAML e mapeamento de namespace para WPF XAML](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
### <a name="type-properties-that-support-typename-as-string"></a>Propriedades de tipo que dão suporte a TypeName como cadeia de caracteres  
 O WPF dá suporte a técnicas que permitem especificar o valor de algumas propriedades do tipo <xref:System.Type> sem a necessidade de um uso de extensão de marcação `x:Type`. Em vez disso, você pode especificar o valor como uma cadeia de caracteres que nomeia o tipo. Exemplos disso são <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> e <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>. O suporte para esse comportamento não é fornecido por meio de conversores de tipo ou extensões de marcação. Em vez disso, esse é um comportamento de adiamento implementado por meio de <xref:System.Windows.FrameworkElementFactory>.  
  
 O Silverlight dá suporte a uma convenção semelhante. Na verdade, o Silverlight atualmente não oferece suporte a `{x:Type}` em seu suporte a idioma XAML e não aceita usos de `{x:Type}` fora de algumas circunstâncias que têm o objetivo de oferecer suporte à migração de XAML do WPF-Silverlight. Portanto, o comportamento de TypeName como cadeia de caracteres é interno a toda a avaliação de propriedade nativa do Silverlight, na qual um <xref:System.Type> é o valor.  
  
## <a name="xaml-2009"></a>XAML 2009  
 O XAML 2009 fornece suporte adicional para tipos genéricos e modifica o comportamento do recurso de `x:TypeArguments` e `x:Type` para fornecer esse suporte.  
  
- `x:TypeArguments` e o elemento de objeto associado para uma instanciação de objeto genérico podem estar em elementos diferentes da raiz. Para obter mais informações, consulte a seção "XAML 2009" da [diretiva x:TypeArguments](x-typearguments-directive.md).  
  
- O XAML 2009 dá suporte a uma sintaxe para especificar a restrição de um tipo genérico na marcação. Isso pode ser usado por `x:TypeArguments`, por `x:Type`ou por dois recursos em combinação.  
  
- A implementação XAML do WPF ao processar o XAML 2009 para carga também adiciona esse recurso ao comportamento de conversão de tipo implícito para determinadas propriedades de estrutura que usam o tipo <xref:System.Type>.  
  
 No WPF, você pode usar os recursos do XAML 2009, mas apenas para XAML flexível (XAML que não é compilado por marcação). O XAML com compilação de marcação para WPF e a forma de BAML do XAML atualmente não dão suporte às palavras-chave e aos recursos do XAML 2009.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Style>
- [Estilo e modelagem](../wpf/controls/styling-and-templating.md)
- [Visão geral de XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)
- [Extensões de marcação e XAML do WPF](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
