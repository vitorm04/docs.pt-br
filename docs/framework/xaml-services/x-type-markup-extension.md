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
ms.openlocfilehash: e4d56c5b5deda0bd1df8827020e0b76cc6276c1c
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46579427"
---
# <a name="xtype-markup-extension"></a>Extensão de marcação x:Type
Fornece o CLR <xref:System.Type> objeto que é o tipo subjacente para um tipo XAML especificado.  
  
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
|`prefix`|Opcional. Um prefixo que mapeia um namespace XAML não padrão. Especificando um prefixo com frequência não é necessário. Consulte Observações.|  
|`typeNameValue`|Necessário. Um nome de tipo que pode ser resolvido para o namespace XAML padrão atual; ou especificado prefixo mapeado se `prefix` for fornecido.|  
  
## <a name="remarks"></a>Comentários  
 O `x:Type` extensão de marcação tem uma função semelhante para o `typeof()` operador em c# ou o `GetType` operador no Microsoft Visual Basic.  
  
 O `x:Type` extensão de marcação fornece um comportamento de conversão de cadeia de caracteres para propriedades que usam o tipo <xref:System.Type>. A entrada é um tipo XAML. A relação entre o tipo de XAML de entrada e saída CLR <xref:System.Type> é que a saída <xref:System.Type> é o <xref:System.Xaml.XamlType.UnderlyingType%2A> da entrada <xref:System.Xaml.XamlType>, depois de pesquisar o necessário <xref:System.Xaml.XamlType> com base no contexto do esquema XAML e o <xref:System.Windows.Markup.IXamlTypeResolver>fornece o contexto de serviço.  
  
 Nos serviços de XAML do .NET Framework, o tratamento para essa extensão de marcação é definido pelo <xref:System.Windows.Markup.TypeExtension> classe.  
  
 Em implementações de estrutura específica, algumas propriedades que recebem <xref:System.Type> como um valor pode aceitar o nome do tipo diretamente (o valor de cadeia de caracteres do tipo `Name`). No entanto, implementar esse comportamento é um cenário complexo. Para obter exemplos, consulte a seção "Observações de uso do WPF" que segue.  
  
 A sintaxe de atributo é a sintaxe mais comum usada com essa extensão de marcação. O token da cadeia de caracteres fornecido após a cadeia de caracteres identificadora `x:Type` é atribuído como o valor <xref:System.Windows.Markup.TypeExtension.TypeName%2A> da classe de extensão subjacente <xref:System.Windows.Markup.TypeExtension>. Sob o contexto de esquema XAML padrão para serviços de XAML do .NET Framework, que se baseia em tipos CLR, o valor desse atributo é o <xref:System.Reflection.MemberInfo.Name%2A> do tipo desejado, ou contém que <xref:System.Reflection.MemberInfo.Name%2A> precedido por um prefixo para um namespace XAML não padrão mapeamento.  
  
 O `x:Type` extensão de marcação pode ser usada na sintaxe de elemento de objeto. Nesse caso, especificando o valor da <xref:System.Windows.Markup.TypeExtension.TypeName%2A> propriedade é necessária para inicializar adequadamente a extensão.  
  
 O `x:Type` extensão de marcação também pode ser usada como um atributo detalhado; no entanto esse uso não é típico: `<object property="{x:Type TypeName=typeNameValue}" .../>`  
  
## <a name="wpf-usage-notes"></a>Notas de uso do WPF  
  
### <a name="default-xaml-namespace-and-type-mapping"></a>Namespace XAML e mapeamento de tipo padrão  
 O namespace XAML padrão para a programação do WPF contém a maioria dos tipos de XAML, que você precisa para cenários típicos de XAML; Portanto, você geralmente pode evitar prefixos ao fazer referência a valores de tipo XAML. Você talvez precise mapear um prefixo se você está fazendo referência a um tipo de um assembly personalizado ou para tipos existentes em um assembly do WPF, mas que são de um namespace CLR que não foi mapeado para o namespace XAML padrão. Para obter mais informações sobre prefixos, namespaces XAML e namespaces CLR de mapeamento, consulte [Namespaces de XAML e mapeamento de Namespace para XAML WPF](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
### <a name="type-properties-that-support-typename-as-string"></a>Esse suporte Typename como cadeia de propriedades de tipo  
 WPF dá suporte a técnicas que permitem especificar o valor de algumas propriedades do tipo <xref:System.Type> sem a necessidade de um `x:Type` uso de extensão de marcação. Em vez disso, você pode especificar o valor como uma cadeia de caracteres que nomeia o tipo. Exemplos são <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> e <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>. Suporte para esse comportamento não é fornecido por meio de extensões de marcação ou conversores de tipo. Em vez disso, isso é implementado por meio de um comportamento de adiamento <xref:System.Windows.FrameworkElementFactory>.  
  
 O Silverlight oferece suporte a uma convenção semelhante. Na verdade, o Silverlight não oferece suporte a `{x:Type}` em seu suporte de linguagem XAML e não aceita `{x:Type}` usos fora algumas circunstâncias que destinam-se para dar suporte à migração de XAML do Silverlight do WPF. Portanto, o comportamento de typename como cadeia de caracteres é incorporado a avaliação de propriedade nativa do Silverlight todos os onde um <xref:System.Type> é o valor.  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 fornece suporte adicional para tipos de genéricos e modifica o comportamento do recurso do `x:TypeArguments` e `x:Type` oferecer esse suporte.  
  
-   `x:TypeArguments` e o elemento de objeto associado para uma instanciação genérica de objeto pode ser em elementos que não seja a raiz. Para obter mais informações, consulte a seção "XAML 2009" [diretiva X:TypeArguments](../../../docs/framework/xaml-services/x-typearguments-directive.md).  
  
-   XAML 2009 dá suporte a uma sintaxe para especificar a restrição de um tipo genérico na marcação. Isso pode ser usado por `x:TypeArguments`, por `x:Type`, ou os dois recursos em combinação.  
  
-   Implementação de XAML WPF durante o processamento de XAML 2009 para carga também adiciona esse recurso para o comportamento de conversão de tipo implícito para determinadas propriedades de estrutura que usam o tipo <xref:System.Type>.  
  
 No WPF, você pode usar os recursos do XAML 2009 mas somente para XAML flexível (XAML não é compilado por marcação). Compilado por marcação XAML para WPF e o formato BAML de XAML têm suporte no momento, as palavras-chave do XAML 2009 e os recursos.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Style>  
 [Estilo e modelagem](../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Visão geral de XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Extensões de marcação e XAML do WPF](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
