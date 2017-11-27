---
title: "Extensão de marcação x:Type"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "27"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: ed0372349a08687fd83b0fc989cc4cb88c29d96c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="xtype-markup-extension"></a>Extensão de marcação x:Type
Fornece o CLR <xref:System.Type> objeto que é o tipo base para um tipo XAML especificado.  
  
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
|`prefix`|Opcional. Um prefixo que mapeia um namespace XAML não padrão. Especificar um prefixo com frequência não é necessário. Consulte Observações.|  
|`typeNameValue`|Necessário. Um nome de tipo pode ser resolvido para o namespace XAML padrão atual; ou o prefixo mapeado se `prefix` for fornecido.|  
  
## <a name="remarks"></a>Comentários  
 O `x:Type` extensão de marcação tem uma função semelhante para o `typeof()` operador em [!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)] ou `GetType` operador em [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)].  
  
 O `x:Type` extensão de marcação fornece um comportamento de conversão de cadeia de caracteres para propriedades que usam o tipo <xref:System.Type>. A entrada é um tipo XAML. A relação entre o tipo de XAML de entrada e saída CLR <xref:System.Type> é que a saída <xref:System.Type> é o <xref:System.Xaml.XamlType.UnderlyingType%2A> da entrada <xref:System.Xaml.XamlType>, depois de pesquisar necessários <xref:System.Xaml.XamlType> com base no contexto do esquema XAML e o <xref:System.Windows.Markup.IXamlTypeResolver>fornece o contexto de serviço.  
  
 Em serviços de XAML do .NET Framework, o tratamento para esta extensão de marcação é definida pelo <xref:System.Windows.Markup.TypeExtension> classe.  
  
 Implementações de estruturas específicas, algumas propriedades que exijam <xref:System.Type> como um valor pode aceitar o nome do tipo diretamente (o valor de cadeia de caracteres do tipo `Name`). No entanto, a implementação esse comportamento é um cenário complexo. Para obter exemplos, consulte a seção "Observações de uso do WPF" que segue.  
  
 A sintaxe de atributo é a sintaxe mais comum usada com essa extensão de marcação. O token da cadeia de caracteres fornecido após a cadeia de caracteres identificadora `x:Type` é atribuído como o valor <xref:System.Windows.Markup.TypeExtension.TypeName%2A> da classe de extensão subjacente <xref:System.Windows.Markup.TypeExtension>. Sob o contexto do esquema padrão XAML para serviços de XAML do .NET Framework, que se baseia em tipos CLR, o valor desse atributo é o <xref:System.Reflection.MemberInfo.Name%2A> do tipo desejado, ou contém que <xref:System.Reflection.MemberInfo.Name%2A> precedido por um prefixo de namespace do XAML não padrão mapeamento.  
  
 O `x:Type` extensão de marcação pode ser usada na sintaxe de elemento de objeto. Nesse caso, especificando o valor de <xref:System.Windows.Markup.TypeExtension.TypeName%2A> propriedade é necessária para inicializar adequadamente a extensão.  
  
 O `x:Type` extensão de marcação também pode ser usada como um atributo detalhado; no entanto esse uso não é comum: `<``object``property``="{x:Type TypeName=``typeNameValue``}" .../>`  
  
## <a name="wpf-usage-notes"></a>Observações de uso do WPF  
  
### <a name="default-xaml-namespace-and-type-mapping"></a>Namespace XAML e mapeamento de tipo padrão  
 O namespace XAML padrão de programação WPF contém a maioria dos tipos de XAML que é necessário para cenários típicos de XAML; Portanto, você geralmente pode evitar prefixos ao fazer referência a valores de tipo XAML. Você precisará mapear um prefixo se você está fazendo referência a um tipo de um assembly personalizado ou para tipos que existem em um assembly do WPF, mas são de um namespace CLR que não foi mapeado para o namespace XAML padrão. Para obter mais informações sobre prefixos, namespaces XAML e namespaces CLR de mapeamento, consulte [Namespaces XAML e o mapeamento de Namespace para WPF XAML](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
### <a name="type-properties-that-support-typename-as-string"></a>Esse suporte Typename como cadeia de propriedades de tipo  
 Técnicas que permitem especificar o valor de algumas propriedades do tipo oferece suporte a WPF <xref:System.Type> sem a necessidade de um `x:Type` uso de extensão de marcação. Em vez disso, você pode especificar o valor como uma cadeia de caracteres que nomeia o tipo. Exemplos são <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> e <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>. Suporte para esse comportamento não é fornecido por meio de conversores de tipo ou extensões de marcação. Em vez disso, este é um comportamento de adiamento implementado por meio de <xref:System.Windows.FrameworkElementFactory>.  
  
 O Silverlight oferece suporte a uma convenção semelhante. Na verdade, o Silverlight não oferece suporte a `{x:Type}` em seu suporte de linguagem XAML e não aceita `{x:Type}` usos fora algumas circunstâncias que pretendem oferecer suporte à migração de XAML do Silverlight do WPF. Portanto, o comportamento de typename como cadeia de caracteres é integrado para todos os avaliação de propriedade nativa do Silverlight em que um <xref:System.Type> é o valor.  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 fornece suporte adicional para genérico, tipos e modifica o comportamento do recurso de `x:TypeArguments` e `x:Type` para oferecer esse suporte.  
  
-   `x:TypeArguments`e o elemento de objeto associado para uma instanciação genérica de objetos pode ser em elementos diferentes de raiz. Para obter mais informações, consulte a seção "XAML 2009" [diretiva X:TypeArguments](../../../docs/framework/xaml-services/x-typearguments-directive.md).  
  
-   XAML 2009 dá suporte a uma sintaxe para especificar a restrição de um tipo genérico na marcação. Isso pode ser usado por `x:TypeArguments`, por `x:Type`, ou os dois recursos em combinação.  
  
-   Implementação de WPF XAML durante o processamento de XAML 2009 para carga também adiciona esse recurso para o comportamento de conversão de tipo implícito para determinadas propriedades de estrutura que usam tipo <xref:System.Type>.  
  
 No WPF, você pode usar recursos XAML 2009 mas somente para XAML livre (XAML não marcação-compilado). Compilação de marcação XAML WPF e do formulário BAML do XAML atualmente não dão os recursos e as palavras-chave de XAML 2009.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Style>  
 [Estilo e modelagem](../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Visão geral de XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Extensões de marcação e XAML WPF](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
